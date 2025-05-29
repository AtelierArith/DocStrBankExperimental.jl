```
assemble!(
    A::AbstractArray{T,2},                  # target matrix
    AP::AssemblyPattern{APT,T,AT};          # BilinearForm Pattern
    apply_action_to::Int = 1,               # action is applied to which argument?
    factor = 1,                             # factor that is multiplied
    transposed_assembly::Bool = false,      # transpose result?
    transpose_copy = Nothing)               # copy a transposed block to this matrix
    where {APT <: APT_BilinearForm, T, AT}
```

Assembly of a BilinearForm BLF into given two-dimensional AbstractArray (e.g. FEMatrixBlock or a ExtendableSparseMatrix).
