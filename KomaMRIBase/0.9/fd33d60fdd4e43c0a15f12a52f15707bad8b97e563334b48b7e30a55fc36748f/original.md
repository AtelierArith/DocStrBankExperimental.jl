```
comp = get_adc_phase_compensation(seq)
```

Returns an array of phase compensation factors, $\exp(-\mathrm{i}\varphi)$, which are used to compensate the acquired signal $S$ by applying the operation $S_{\mathrm{comp}} = S \exp(-\mathrm{i}\varphi)$ after the simulation. This compensation is necessary because the signal typically exhibits a phase offset of $\varphi$ following RF excitation with a phase of $\varphi$. Such pulses are commonly employed in sequences involving RF spoiling.

# Arguments

  * `seq`: (`::Sequence`) sequence struct

# Returns

  * `comp`: (`::Vector{Complex}`, `[rad]`) array of phase compensations for every acquired sample
