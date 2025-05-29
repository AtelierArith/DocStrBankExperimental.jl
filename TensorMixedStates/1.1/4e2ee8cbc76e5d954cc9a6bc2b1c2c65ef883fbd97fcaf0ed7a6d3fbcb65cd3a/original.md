```
runTMS(::SimData)
runTMS(::SimData; clean = true)
runTMS(::SimData; restart = true)
runTMS(::SimData; output = myoutput)
```

run the given simulation (see SimData for details), write the output to file and return a Simulation object containing the result. `clean` (default `false`) remove the simulation directory and exit, `restart` (default `false`) remove the simulation directory and run the simulation, `output` redirect all output to the given IO channel (no output directory created), usefull values are stdout or devnull (to suppress all output). `save_json` (default `true`) save the data accumulated in dicts in JSON format in the corresponding files
