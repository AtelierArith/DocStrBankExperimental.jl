```
acn(x, snr_dB, fs, color = :pink; band_freq = Float64[], rst = true)
```

Adds a complex Colored Noise (ACN) to a signal `x` with a given SNR

**Inputs**

  * `x`: Signal
  * `snr_dB`: Signal to noise ratio [dB]
  * `fs`: Sampling frequency [Hz]
  * `color`: Color of the noise

      * `:white`
      * `:pink` (default)
      * `:blue`
      * `:brown`
      * `:purple`
  * `band_freq`: Frequencies used to defined the bandpass filter applied to the colored noise
  * `rst`: Reset the random number generator

**Output**

  * `y`: Noisy signal
