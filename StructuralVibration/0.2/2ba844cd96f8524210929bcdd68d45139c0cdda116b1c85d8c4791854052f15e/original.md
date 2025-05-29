```
mgwn(x, snr_dB; rst = true)
```

Adds a multiplicative Gaussian White Noise (MGWN) to a signal `x` with a given SNR

**Inputs**

  * `x`: Signal
  * `snr_dB`: Signal to noise ratio [dB]
  * `rst`: Reset the random number generator

**Output**

  * `y`: Noisy signal
