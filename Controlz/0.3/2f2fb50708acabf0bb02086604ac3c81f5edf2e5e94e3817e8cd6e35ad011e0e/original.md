```
margins = gain_phase_margins(g_ol, ω_c_guess=0.001, ω_g_guess=0.001)
```

compute critical frequency (radians / time), gain crossover frequency (radians / time),  gain margin, and phase margin (radians) of a closed loop, given its closed loop transfer function `g_ol::TransferFunction`.

if ω*c or ω*g is not found (i.e. if either are `NaN`), but the `bode_plot` clearly shows  a critical/gain crossover frequency, adjust `ω_c_guess` or `ω_g_guess` to find the root.

# Example

```
g_ol = 2 * exp(-s) / (5 * s + 1)
margins = gain_phase_margins(g_ol)
margins.ω_c # critical freq. (radians / time)
margins.ω_g # gain crossover freq. (radians / time)
margins.gain_margin # gain margin
margins.phase_margin # phase margin (radians)
```
