```
get_looptransfer(sys, ap::AnalysisPoint; kwargs)
get_looptransfer(sys, ap_name::Symbol; kwargs)
```

Compute the (linearized) loop-transfer function in analysis point `ap`, from `ap.out` to `ap.in`.

!!! info "Negative feedback"
    Feedback loops often use negative feedback, and the computed loop-transfer function will in this case have the negative feedback included. Standard analysis tools often assume a loop-transfer function without the negative gain built in, and the result of this function may thus need negation before use.


# Arguments:

  * `kwargs`: Are sent to `ModelingToolkit.linearize`

See also [`get_sensitivity`](@ref), [`get_comp_sensitivity`](@ref), [`open_loop`](@ref).
