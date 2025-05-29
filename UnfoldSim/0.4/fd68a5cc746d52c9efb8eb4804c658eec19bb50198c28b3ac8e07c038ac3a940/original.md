```
PuRF(; n = 10.1, tmax = 0.93, sfreq = 100)
```

Default generator for PuRF Pupil Response Function. The canonical PRF is a gamma function and implemented according to Denison 2020 equation (2) going back to Hoeks & Levelt, 1993.

The pupil response is evaluated at t = 0:1/sfreq:3*tmax. The response is normalized by the peak-maximum at tmax, thus typically a pupil-response of 1 is returned (disregarding numerical issues).

# Keyword arguments:

  * `n = 10.1`: shape parameter
  * `tmax = 0.93`: peak maximum
  * `sfreq = 100`: sampling frequency

# Returns

  * `Vector`: canonical pupil response with length(0:1/sfreq:3*tmax) entries.

# Examples

```julia-repl
julia> PuRF(; n = 5)
280-element Vector{Float64}:
 0.0
 2.0216617815131253e-8
 6.130689396024061e-7
 4.4118063684811444e-6
 1.761817666835793e-5
 ⋮
 0.012726253506722554
 0.012280989091455786
 0.011850525657416842
 0.011434405338911133
 0.011032182932283816
```
