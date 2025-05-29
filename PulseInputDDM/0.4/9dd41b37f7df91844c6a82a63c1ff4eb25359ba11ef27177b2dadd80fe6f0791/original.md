```
process_spike_data(μ_rnt, data)
```

Arguments:

  * `μ_rnt`: `array` of Gaussian-filterd single trial firing rates for all cells and all trials in one session. `μ_rnt` is output from `load_neural_data`.
  * `data`: `array` of all trial data for one session. `data` is output from `load_neural_data`.

Optional arguments: 

  * `nconds`: number of groups to make to compute PSTHs

Returns: 

  * `μ_ct`: mean PSTH for each group.
  * `σ_ct`: 1 std PSTH for each group.
