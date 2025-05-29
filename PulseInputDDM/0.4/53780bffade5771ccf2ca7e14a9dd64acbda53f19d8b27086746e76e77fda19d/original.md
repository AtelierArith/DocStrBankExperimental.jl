```
neuraldata
```

Module-defined class for keeping data organized for the `neuralDDM` model.

Fields:

  * `input_data`: stuff related to the input of the accumaltor model, i.e. clicks, etc.
  * `spikes`: the binned spikes
  * `ncells`: numbers of cells on that trial (should be the same for every trial in a session)
  * `choice`: choice on that trial
