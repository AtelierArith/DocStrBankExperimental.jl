```
  simplest_rational_inside(x::RealFieldElem)
```

Return the simplest fraction inside the ball $x$. A canonical fraction $a_1/b_1$ is defined to be simpler than $a_2/b_2$ iff $b_1 < b_2$ or $b_1 = b_2$ and $a_1 < a_2$.

# Examples

```jldoctest
julia> RR = RealField()
Real field

julia> simplest_rational_inside(const_pi(RR))
8717442233//2774848045
```
