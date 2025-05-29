```
acn(x, snr_dB, freq, color = :pink; rst = true)
```

Adds a complex Random Colored Noise (ACN) to a signal `x` with a given SNR

**Inputs**

  * `x::VecOrMat{Real}`: Signal
  * `snr_dB`: Signal to noise ratio [dB]
  * `freq::AbstractVector`: Frequency range of interest
  * `color`: Color of the noise

      * `:white`
      * `:pink` (default)
      * `:blue`
      * `:brown`
      * `:purple`
  * `rst::Bool`: Reset the random number generator

**Output**

  * `y`: Noisy signal
