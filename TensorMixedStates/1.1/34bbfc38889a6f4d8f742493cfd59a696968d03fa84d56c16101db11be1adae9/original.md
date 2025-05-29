```
get_sim_file(::Simulation, filename)
```

return the corresponding file of the given simulation "stdout" (or "-"), "stderr" and "" respectively redirect to stdout, stderr and devnull, other names are interpreted as file names.

Filename finishing by ".json" will return a Dict where to store data and this data will be output in JSON format in the file by `runTMS` at the end.
