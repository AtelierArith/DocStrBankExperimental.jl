```
compose(G::Union{AbstractSystem,System}, F::Union{AbstractSystem,System})
```

Construct the composition $G(F(x))$. You can also use the infix operator `∘` (written by \circ).

### Example

```julia
julia> @var a b c x y z

julia> g = System([a * b * c]);

julia> f = System([x+y, y + z, x + z]);

julia> compose(g, f)
Composition G ∘ F:
F:
ModelKitSystem{(0xbb16b481c0808501, 1)}:
Compiled: System of length 3
 3 variables: x, y, z

 x + y
 y + z
 x + z

G:
ModelKitSystem{(0xf0a2384a42428501, 1)}:
Compiled: System of length 1
 3 variables: a, b, c

 a*b*c


julia> (g ∘ f)([x,y,z])
1-element Array{Expression,1}:
 (x + z)*(y + z)*(x + y)
```
