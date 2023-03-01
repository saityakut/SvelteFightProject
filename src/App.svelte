<script>
  import { Progress } from "sveltestrap";

  $: playerOneValue = 100;
  $: playerTwoValue = 100;
  $: logs = [];
  let message = "";

  const handleAttackClick = () => {
    let randomNumber1 = Math.floor(Math.random() * 16);
    if (playerOneValue - randomNumber1 > 0) {
      playerOneValue -= randomNumber1;
      message = `player one lost ${randomNumber1} score`;
      logs.unshift(message);
      logs = logs;
    } else {
      playerOneValue = 0;
      message = "Player one is lost unfourtanelty";
      logs.unshift(message);
      logs = logs;
      if (confirm("Player one is lost unfourtanelty")) {
        playerOneValue = 100;
        playerTwoValue = 100;
        logs = [];
      }
    }
    let randomNumber2 = Math.floor(Math.random() * 16);
    if (playerTwoValue - randomNumber2 > 0) {
      playerTwoValue -= randomNumber2;
      message = `player two lost ${randomNumber2} score`;
      logs.unshift(message);
      logs = logs;
    } else {
      playerTwoValue = 0;
      message = "Player two is lost unfourtanelty";
      logs.unshift(message);

      logs = logs;
      if (confirm("Player two is lost unfourtanelty")) {
        playerOneValue = 100;
        playerTwoValue = 100;
        logs = [];
      }
    }
    //logs = logs.push(message);
    console.log(logs);
  };
  const handleUltiAttackClick = () => {
    let randomNumber1 = Math.floor(Math.random() * 51);
    if (playerTwoValue - randomNumber1 > 0) {
      playerTwoValue -= randomNumber1;
      message = `player two lost ${randomNumber1} score`;
      logs.unshift(message);
      logs = logs;
    } else {
      playerTwoValue = 0;
      message = `player two lost unfourtanelty`;
      logs.unshift(message);
      logs = logs;
      if (confirm("Player two is lost unfourtanelty")) {
        playerOneValue = 100;
        playerTwoValue = 100;
        logs = [];
      }
    }
    let randomNumber2 = Math.floor(Math.random() * 16);
    if (playerOneValue - randomNumber2 > 0) {
      playerOneValue -= randomNumber2;
      message = `player one lost ${randomNumber2} score`;
      logs.unshift(message);
      logs = logs;
    } else {
      playerOneValue = 0;
      message = `player one lost ${randomNumber1} score`;
      logs.unshift(message);
      logs = logs;
      if (confirm("Player one is lost unfourtanelty")) {
        playerOneValue = 100;
        playerTwoValue = 100;
        logs = [];
      }
    }
  };
</script>

<div class="container text-center">
  <div class="row">
    <div class="col-sm-6 col-md-6 col-lg-6">
      <h3 class="text-danger">Player One</h3>
      <Progress value={playerOneValue} color="danger" class="my-1" />
      <h6>Player One Life : {playerOneValue}%</h6>
    </div>

    <div class="col-sm-6 col-md-6 col-lg-6">
      <h3 class="text-success">Player Two</h3>
      <Progress value={playerTwoValue} color="success" class="my-1" />
      <h6>Player Two Life : {playerTwoValue}%</h6>
    </div>
  </div>
  <button on:click={handleAttackClick} class="my-3 btn btn-primary "
    >Attack</button
  >
  <button on:click={handleUltiAttackClick} class="my-3 btn btn-danger "
    >Ulti Attack</button
  >

  <div class="col-12 text-center">
    {#each logs as log}
      <h5 class="text-primary">{log}</h5>
    {/each}
  </div>
</div>

<style>
  button {
    width: 40%;
  }
</style>
