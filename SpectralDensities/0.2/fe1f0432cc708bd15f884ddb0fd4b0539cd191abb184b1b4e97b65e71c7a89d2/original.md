```
memory_kernel(J::AbstractSD, τ)
```

Calculate the memory kernel for a spectral density `J` at a given time delay `τ`, that is

$$
\mathcal{K}(\tau) = 2\Theta(\tau)\int_0^\infty J(\omega)\sin(\omega)\mathrm{d}\omega,
$$

where $\Theta$ is the Heavisde theta function.

# Arguments

  * `J::AbstractSD`: The spectral density.
  * `τ`: The time delay at which the memory kernel is evaluated.

# Returns

  * The memory kernel for the spectral density `J` at the given time delay `τ`.
