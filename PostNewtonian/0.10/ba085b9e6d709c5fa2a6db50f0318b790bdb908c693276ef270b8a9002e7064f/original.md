```
uniform_in_phase(solution, saves_per_orbit)
```

Interpolate `solution` to uniform steps in phase.

By default, the `solution` returned by [`orbital_evolution`](@ref) may be sampled very sparsely — too sparsely to satisfy the Nyquist limit of the waveform.  If the waveform extends to $\ell_{\mathrm{max}}$, there will be modes varying slightly more rapidly than $\exp\left(\pm i\, \ell_{\mathrm{max}}\, \Phi \right)$, where $\Phi$ is the orbital phase.  If the frequency were constant, this would require at least $2\ell_{\mathrm{max}}$ samples per orbit.  To incorporate a safety factor, $4\ell_{\mathrm{max}}$ seems to work fairly reliably.

See also the `saves_per_orbit` and `saveat` arguments to [`orbital_evolution`](@ref), as well as interpolation-in-time capabilities of the result of that function.
