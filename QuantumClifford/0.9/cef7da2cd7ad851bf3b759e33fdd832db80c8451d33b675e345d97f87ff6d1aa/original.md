```julia
canonicalize_rref!(
    state::QuantumClifford.AbstractStabilizer,
    colindices;
    phases
) -> Tuple{QuantumClifford.AbstractStabilizer, Any}

```

Canonicalize a stabilizer (in place) along only some columns.

This uses different canonical form from [`canonicalize!`](@ref). It also indexes in reverse in order to make its use in [`traceout!`](@ref) more efficient. Its use in `traceout!` is its main application.

It returns the (in place) modified state and the index of the last pivot.

Based on [audenaert2005entanglement](@cite).

See also: [`canonicalize!`](@ref), [`canonicalize_gott!`](@ref)
