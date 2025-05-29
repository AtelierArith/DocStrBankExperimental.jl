```
displace_analytical(alpha::Number, n::Integer, m::Integer)
```

Get a specific matrix element of the (analytical) displacement operator in the Fock basis: `Dmn = ⟨n|D̂(α)|m⟩`. The precision used for computation is based on the type of `alpha`. If `alpha` is a Float64, ComplexF64, or Int, the computation will be carried out at double precision.
