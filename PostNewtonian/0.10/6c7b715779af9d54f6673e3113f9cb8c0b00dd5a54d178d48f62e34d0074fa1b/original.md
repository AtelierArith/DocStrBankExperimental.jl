```
coorbital_waveform(inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
coorbital_waveform(inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

Evaluate the post-Newtonian waveform mode weights in the co-orbital frame for the given `inspiral` output by [`orbital_evolution`](@ref).

See also [`inertial_waveform`](@ref) for the waveform in the inertial frame.

For a detailed description of the format and physical interpretation of the returned quantity, see the ["Waveforms" section of the manual.](https://moble.github.io/PostNewtonian.jl/stable/internals/waveforms.html)

The `PNOrder` defaults to the one used to compute `inspiral`, but may be changed by passing the keyword argument.

!!! tip
    If you need this waveform at a different set of times `t′` than is currently present in `inspiral.t`, you should use the built-in interpolation capabilities of `inspiral` *first*, as in `inspiral′ = inspiral(t′)`, rather than interpolating the results of this function.  Or, perhaps better yet, you could select the times when calling `orbital_evolution` by using the `saves_per_orbit` or `saveat` keyword argument to that function.  These approaches will be more accurate, faster, and require less memory than interpolating the result of this function.  If using `saves_per_orbit`, you probably want to set it to *at least* `2ℓₘₐₓ`, or preferably `4ℓₘₐₓ`.


The mode weights are given starting at `ℓₘᵢₙ` (which must satisfy `0 ≤ ℓₘᵢₙ ≤ 2`) and extending through `ℓₘₐₓ`.  The waveform is returned as a 2-dimensional `Array`, in which the first index varies over the mode index from `(ℓ, m) = (ℓₘᵢₙ, -ℓₘᵢₙ)` to `(ℓ, m) = (ℓₘₐₓ, ℓₘₐₓ)`, with `m` varying most rapidly, and the second index varying over the time steps.

In this function, the waveform is returned in the co-orbital frame — which is somewhat like the co-rotating frame.  In particular, the modes of non-precessing systems vary slowly, over inspiral timescales; modes of precessing systems still vary on orbital timescales, though even this variation could be factored out.
