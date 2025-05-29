```
ConnectingOrbit(Na::Integer, p::Integer)
```

Initialize a connecting orbit consisting of `p` segments cⱼ : [0,1] -> R². The endpoints cⱼ(0) and cⱼ(1) are both hyperbolic perodic orbits. The connecting orbits connect these, acting as the outer boundary of an island. The connecting orbits are parameterized by Chebyshev polynomials of degree `Na`.

See `linear_initial_connecting_orbit` and `gn_connecting!` for functions to initialize and compute a connecting orbit.
