```
(value, sigma) = snr(G1::GraphSig, G2::GraphSig, stdp::Bool = false)

Compute the SNR between G1 (original signal) and G2 (noisy signal)
```

### Input Arguments

  * `G1::GraphSig`: Original reference graph signal
  * `G2::GraphSig`: Restored or noisy graph signal
  * `stdp::Bool`: A flag to specify to compute the standard deviation of the difference

### Output Arguments

  * `value`: Signal/Noise Ratio in the dB unit
  * `sigma`: the standard deviation of the noise (if stdp == true)
