```
calc_v_set(wc::WinchController, v_act, force, f_low; v_set_pc=nothing)
```

Calculate the set velocity (`v_set`) for the winch.

# Arguments

  * `wc::WinchController`: The winch controller instance.
  * `v_act`: The actual velocity of the winch.
  * `force`: The measured or estimated force on the winch.
  * `f_low`: The lower force threshold.
  * `v_set_pc`: (optional) Precomputed or externally provided set velocity. Defaults to `nothing`.

# Returns

  * The calculated set velocity for the winch.

# Notes

  * The function logic depend on the relationship between the actual force and the lower force threshold.
  * If `v_set_pc` is provided, it overrides the computed set velocity.
