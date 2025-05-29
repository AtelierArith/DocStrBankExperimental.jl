```
agwn(x, snr_dB; rst = true)
```

Adds a Gaussian White Noise (AGWN) to a signal `x` with a given SNR.

**Inputs**

  * `x`: Signal (Real or Complex)
  * `snr_dB`: signal to noise ratio [dB]
  * `rst`: Reset the random number generator - Bool

**Output**

  * `y`: Noisy signal
