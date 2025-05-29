```
rmeye(
    n::Integer;
    backend::Backend = CPU(),
    float_type::Type{Tv} = Float32,
    int_type::Type{Ti} = Int)::RefinementMatrix{Tv, Ti} where {Tv, Ti <: Integer}
```

Construct an identity refinement matrix.

## Input

  * `n`: The size of the identity matrix is n×n
  * `backend`: The KernelAbstractions backend of the matrix data
  * `float_type`: The value type of the matrix data
  * `int_type`: The integer type of the matrix data
