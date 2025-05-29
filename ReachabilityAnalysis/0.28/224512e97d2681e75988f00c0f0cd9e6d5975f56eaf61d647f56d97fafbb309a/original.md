```
HACLD1{T<:AbstractSystem, MT, N, J} <: AHACLD
```

Single-mode hybrid automaton with clocked linear dynamics.

### Fields

  * `sys`       – system
  * `rmap`      – reset map
  * `Tsample`   – sampling time
  * `ζ`         – jitter
  * `switching` – (optional) value that

### Notes

This type is parametric in:

  * `T`  – system type
  * `MT` – type of the reset map
  * `N`  – numeric type, applies to the sampling time and jitter
  * `J`  – type associated to the jitter

The type associated to the jitter, `J`, can be one of the following:

  * `Missing`     – no jitter, i.e. switchings are deterministic
  * `Number`      – symmetric jitter, i.e. non-deterministic switchings occur in the                  intervals `[Tsample - ζ, Tsample + ζ]`
  * `IA.Interval` – non-symmetric jitter, i.e. non-deterministic switchings occur in the                  intervals `[Tsample + inf(ζ), Tsample + sup(ζ)]`; note that                  the infimum is expected to be negative for most use cases, i.e.                  when the jitter interval is centered at zero

The following getter functions are available:

  * `initial_state`  – initial state of the continuous mode
  * `jitter`         – return the jitter
  * `reset_map`      – return the reset map
  * `sampling_time`  – return the sampling time
  * `statedim`       – dimension of the state-space
  * `system`         – return the continuous mode
  * `switching`      – return the type of switching

Non-deterministic switching:

tstart       Ts-ζ⁻         tend  [––––––-|––––––-]

In the following, suppose that the continuous post-operator has fixed step-size `δ > 0`. If `F` denotes the flowpipe, then

F[1]    F[2]    F[3]    F[4]    F[5]        F[k] [–––][–––][–––][–––][–––]  ⋅ ⋅ ⋅ ⋅ ⋅ ⋅ ⋅ ⋅  [–––]

`R = array(F)` denote the array of reach-sets time-span for reach reach-set is of the form:

Similarly we compute tstart and tend for the supremum part Ts-ζ⁺
