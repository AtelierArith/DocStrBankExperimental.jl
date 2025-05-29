```
planck_wave(wavelength, temperature) -> black_body_flux
```

### Purpose

Calculate the flux of a black body per unit wavelength.

### Explanation

Return the spectral radiance of a black body per unit wavelength using [Planck's law](https://en.wikipedia.org/wiki/Planck%27s_law)

$$
B_λ(λ, T) = \frac{2hc^2}{λ^5} \frac{1}{e^{\frac{hc}{λ k_\mathrm{B}T}} - 1}
$$

### Arguments

  * `wavelength`: wavelength at which the flux is to be calculated, in meters.
  * `temperature`: the equilibrium temperature of the black body, in Kelvin.

### Output

The spectral radiance of the black body, in units of W/(sr·m³).

### Example

Plot the spectrum of a black body in $[0, 3]$ µm at $5000$ K.  Use [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) for plotting.

```julia
using Plots
wavelength = range(0, stop=3e-6, length=1000);
temperature = ones(wavelength)*5000;
flux = planck_wave.(wavelength, temperature);
plot(wavelength, flux)
```

### Notes

`planck_freq` calculates the flux of a black body per unit frequency.

Code of this function is based on IDL Astronomy User's Library.
