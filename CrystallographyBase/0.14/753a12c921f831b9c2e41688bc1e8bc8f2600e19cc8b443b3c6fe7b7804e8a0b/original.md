```
Lattice(a, b, c, α, β, γ; axis = :a)
```

Construct a `Lattice` from the six cell parameters.

The default convention we used here is that edge vector 𝐚 in the positive x-axis direction, edge vector 𝐛 in the x-y plane with a positive y-axis component, and edge vector 𝐜 with a positive z-axis component in the Cartesian system. See [Wikipedia](https://en.wikipedia.org/w/index.php?title=Fractional_coordinates&oldid=961675499#In_crystallography). You can also choose `axis = :c`.
