```
simulate_expected_firing_rate(model)
```

Given a `model` generate samples of the firing rate `λ` of each neuron.

Arguments:

  * `model`: an instance of a `neuralDDM`.

Optional arguments:

  * `num_samples`: How many independent samples of the latent to simulate, to average over.

Returns:

  * `λ`: an `array` is length `num_samples`. Each entry an `array` of length number of trials. Each entry of that is an `array` of length number of neurons. Each entry of that is the firing rate of that neuron on that trial for some length of time.
  * `μ_λ`: the mean firing rate for each neuron (averaging across the noise of the latent process for `num_samples` trials).
  * `μ_c_λ`: the average across trials and across group with similar evidence values (grouped into `nconds` number of groups).
