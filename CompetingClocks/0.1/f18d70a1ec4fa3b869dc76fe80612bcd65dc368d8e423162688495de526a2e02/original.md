```
misscount(recorder::CommonRandomRecorder)
```

The common random recorder watches a simulation and replays the states of the random number generator on subsequent runs. This counts the number of times during the most recent run that a clock event happened that could not be replayed.
