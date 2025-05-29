```
assemble!(
    b::Union{AbstractArray{T,1},AbstractArray{T,2}},    # target vector/matrix
    AP::AssemblyPattern{APT,T,AT};                      # LinearForm pattern
    factor = 1)                                         # factor that is multiplied
    where {APT <: APT_LinearForm, T, AT}
```

Assembly of a LinearForm pattern AP into a vector or matrix (if action is vetor-valued).
