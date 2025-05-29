```
applydynamics!(spin, BtoM, A, [B])
```

Apply dynamics to the given spin, overwriting the spin's magnetization vector. `BtoM` is used to store intermediate results (and is thus overwritten).

# Examples

```jldoctest
julia> s = Spin(1, 1000, 100, 3.75); s.M
Magnetization vector with eltype Float64:
 Mx = 0.0
 My = 0.0
 Mz = 1.0

julia> BtoM = Magnetization();

julia> (A,) = excite(s, InstantaneousRF(π/2)); applydynamics!(s, BtoM, A); s.M
Magnetization vector with eltype Float64:
 Mx = 1.0
 My = 0.0
 Mz = 6.123233995736766e-17

julia> (A, B) = freeprecess(s, 100); applydynamics!(s, BtoM, A, B); s.M
Magnetization vector with eltype Float64:
 Mx = -0.2601300475114444
 My = -0.2601300475114445
 Mz = 0.09516258196404054
```
