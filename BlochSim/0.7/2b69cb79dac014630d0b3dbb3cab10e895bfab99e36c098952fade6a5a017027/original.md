```
combine!(A, B, A1, B1, A2, B2)
combine!(A, A1, A2)
```

Combine the matrices and vectors that describe the dynamics of a spin into one matrix and one vector, overwriting `A` and `B`. The dynamics described by `A1` and `B1` apply first, then those described by `A2` and `B2`. In other words, `A = A2 * A1` and `B = A2 * B1 + B2`.

# Examples

```jldoctest
julia> s = Spin(1, 1000, 100, 3.75);

julia> A = BlochMatrix(); B = Magnetization();

julia> (A1, B1) = excite(s, InstantaneousRF(π/2));

julia> (A2, B2) = freeprecess(s, 100);

julia> combine!(A, B, A1, B1, A2, B2); A * s.M + B
Magnetization vector with eltype Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404054
```
