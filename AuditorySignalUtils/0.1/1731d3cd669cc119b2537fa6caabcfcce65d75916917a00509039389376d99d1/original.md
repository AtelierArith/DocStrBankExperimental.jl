```
te_noise(; kwargs...)
```

Synthesize threshold-equalizing noise (Moore et al., 2000)

Synthesize threshold-equalizing noise (TEN), based on code adapted from from original code from lab of A. J. Oxenham. TEN is originally described in:

Moore, B. C. J., Huss, M., Vickers, D. A., Glasberg, B. R., and Alcántra, J. I. (2000). “A test for the diagnosis of dead regions in the cochlea,” British Journal of Audiology, 34, 205–224. doi:10.3109/03005364000000131

TEN is a noise spectrally shaped so as to acheive uniform masked thresholds for a pure tone as a function of frequency from 125–15000 Hz. TEN is produced under the assumption that the power of a signal at masked threshold is:

```
P₀ = N₀ × K × ERB
```

where N₀ is the noise power spectral density, K is the signal-to-noise ratio at the output  of the auditory filter required for masked threshold at the given frequency (this varies with frequency), and ERB is the equivalent rectangular bandwidth of the auditory filter at the given frequency.

Note that TEN level usually refers to level in the ERB centered at 1 kHz, and NOT overall level. 

# Arguments:

  * `freq_low=0.25e3`: Lower cutoff of the noise passband (Hz)
  * `freq_high=15e3`: Upper cutoff of the noise passband (Hz)
  * `level=20.0`: Level in the 1 kHz ERB before the ramp is applied (dB SPL)
  * `dur=1.0`: Total duration, including ramps (s)
  * `dur_ramp=0.01`: Ramp duration (s)
  * `fs=100e3`: Sampling rate (Hz)
