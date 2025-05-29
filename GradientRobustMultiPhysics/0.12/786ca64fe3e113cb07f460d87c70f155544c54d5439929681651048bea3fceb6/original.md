```
full_assemble!(
    A::AbstractArray{T,2},                 # target matrix
    b::AbstractArray{T,1},                 # target rhs
    AP::AssemblyPattern{APT,T,AT};         # NonlinearForm pattern
    FEB::Array{<:FEVectorBlock,1};         # coefficients of current solution for each operator
    factor = 1,                            # factor that is multiplied
    transposed_assembly::Bool = false)     # transpose result?
    where {APT <: APT_NonlinearForm, T, AT}
```

Assembly (of Newton terms) of a NonlinearForm assembly pattern (assembles both matrix and rhs!).
