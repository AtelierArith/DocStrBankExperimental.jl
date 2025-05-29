function measure_noisy

```
This function mimicks YaoAPI.measure with noisy readout
```

# Arguments

  * reg: statevector representing the quantum state to be measured
  * noise_model: an ErrorModel struct which contains a method to create the confusion matrix
  * site (optional): site to be measured
  * nshots (optional kwarg): number of measurements to return
