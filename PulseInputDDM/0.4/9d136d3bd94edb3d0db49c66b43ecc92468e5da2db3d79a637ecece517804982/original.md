```
load_neural_data(file::Vector{String}; centered, dt, delay, pad, filtSD, extra_pad, cut, pcut)
```

Calls `load_neural_data` for each entry in `file` and then creates three array outputs—`spike_data`, `μ_rnt`, `μ_t`—where each entry of an array is the relevant data for a single session. 

Returns:

  * `data`: an `array` of length number of session. Each entry is for a session, and is another `array`. Each entry of the sub-array is the relevant data for a trial.
  * `μ_rnt`: an `array` of length number of sessions. Each entry is another `array` of length number of trials. Each entry of the sub-array is also an `array`, of length number of cells. Each entry of that array is the filtered single-trial firing rate of each neuron
  * `μ_t`: an `array` of length number of sessions. Each entry is an `array` of length number of cells. Each entry is the trial-averaged firing rate (across all trials).
