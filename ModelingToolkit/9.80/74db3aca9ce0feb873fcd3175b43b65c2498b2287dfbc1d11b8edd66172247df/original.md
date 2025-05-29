```
get_comp_sensitivity(sys, ap::AnalysisPoint; kwargs)
get_comp_sensitivity(sys, ap_name::Symbol; kwargs)
```

Compute the complementary sensitivity function in analysis point `ap`. The complementary sensitivity function is obtained by introducing an infinitesimal perturbation `d` at the output of `ap`, linearizing the system and computing the transfer function between `d` and the input of `ap`.

# Arguments:

  * `kwargs`: Are sent to `ModelingToolkit.linearize`

See also [`get_sensitivity`](@ref), [`get_looptransfer`](@ref).
