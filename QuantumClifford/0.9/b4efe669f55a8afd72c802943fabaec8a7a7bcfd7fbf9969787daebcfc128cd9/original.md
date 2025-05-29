```julia
project!(
    state::QuantumClifford.MixedStabilizer,
    pauli::QuantumClifford.PauliOperator;
    phases
) -> Tuple{QuantumClifford.MixedStabilizer, Int64, Any}

```

When using [`project!`](@ref) on [`MixedStabilizer`](@ref) it automates some of the extra steps we encounter when implicitly using the `Stabilizer` datastructure to represent mixed states. Namely, it helps when the projector is not among the list of stabilizers:

```jldoctest
julia> s = S"XZI
             IZI";


julia> ms = MixedStabilizer(s)
+ X__
+ _Z_

julia> project!(ms, P"IIY")[1]
+ X__
+ _Z_
+ __Y
```

Similarly to [`project!`](@ref) on [`Stabilizer`](@ref), this function has cubic complexity when the Pauli operator commutes with all rows of the tableau. Most of the time it is better to simply use [`MixedDestabilizer`](@ref) representation.

Unlike other `project!` methods, this one does not allow for `keep_result=false`, as the correct rank or anticommutation index can not be calculated without the expensive (cubic) canonicalization operation required by `keep_result=true`.

See the "Datastructure Choice" section in the documentation for more details.

See also: [`projectX!`](@ref), [`projectY!`](@ref), [`projectZ!`](@ref).
