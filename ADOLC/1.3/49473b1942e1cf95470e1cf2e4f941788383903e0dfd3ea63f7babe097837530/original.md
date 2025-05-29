```
create_cxx_identity(n::I_1, m::I_2) where {I_1 <: Integer, I_2 <: Integer}
```

Creates a identity matrix of shape (`n`, `m`) of type CxxPtr{CxxPtr{Float64}} (wrapper of C++'s double**).

# Example

```jldoctest
id = CxxMatrix(create_cxx_identity(2, 4), 2, 4)


# output

2×4 CxxMatrix:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
```
