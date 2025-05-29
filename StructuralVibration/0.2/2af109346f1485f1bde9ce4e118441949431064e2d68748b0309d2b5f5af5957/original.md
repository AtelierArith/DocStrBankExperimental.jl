```
mixed_noise(x, snr_dB; rst = true)
```

Adds both additive and multiplicative Gaussian White Noise to a signal `x` with a given SNR

**Inputs**

  * `x`: Signal
  * `snr_dB`: Signal to noise ratio [dB]
  * `rst`: Reset the random number generator

**Output**

  * `y`: Noisy signal
