```
Momentum(component=0; fold=true) <: AbstractHamiltonian
```

The momentum operator $P̂$.

The component argument controls which component of the address is taken into consideration. A value of 0 sums the contributions of all components. If `fold` is true, the momentum is folded into the Brillouin zone.

```jldoctest
julia> address = BoseFS((1, 0, 2, 1, 2, 1, 1, 3))
BoseFS{11,8}(1, 0, 2, 1, 2, 1, 1, 3)

julia> v = DVec(address => 10);

julia> rayleigh_quotient(Momentum(), DVec(address => 1))
-2.0

julia> rayleigh_quotient(Momentum(fold=false), DVec(address => 1))
14.0
```
