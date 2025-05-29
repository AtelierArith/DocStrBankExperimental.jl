```
timmer_koenig(psd, rng::random.AbstractRNG, alternative=false)
```

Generate a time series with a given power spectral density (PSD) using the [1995A&A...300..707T](@cite) method

1. Given N values of the power spectral density (PSD) 𝓟
2. Draw 2N values from a standard normal distribution.
3. The amplitude of the randomised periodogram is given by A = N + i M
4. The randomised periodogram is given by 𝓟_rand = √(𝓟 / 2) * A
5. The first value of the randomised periodogram inserted and set to 0
6. The time series is obtained by taking the inverse Fourier transform of the randomised periodogram, with the function FFTW.irfft. We use the length of the time series as 2*(N+1)-1.

The alternative parametrisation is given by

1. Given N values of the power spectral density (PSD) 𝓟
2. Draw N-1 values from a χ²(2)  distribution and 1 value from χ²₁(1), this is A the amplitude of the randomised periodogram
3. Draw N values from a uniform distribution between 0 and 1, and set the last value to 0, this is θ the phase of the randomised periodogram
4. The randomised periodogram is given by 𝓟_rand = √(𝓟 / 2 * A) * exp(2πiθ)
5. The first value of the randomised periodogram inserted and set to 0
6. The time series is obtained by taking the inverse Fourier transform of the randomised periodogram, with the function FFTW.irfft. We use the length of the time series as 2*(N+1)-1.

# Arguments

  * `𝓟::Array{Float64, 1}`: PSD associated with the process
  * `rng::Random.AbstractRNG`: Random number generator.
  * `α::Real`: Multiplicative factor for the randomised periodogram. Default is 1.0. This can be a complex vector to add a phase to the time series.

# Returns

  * `x::Array{Float64, 1}`: Time series with the given PSD.
