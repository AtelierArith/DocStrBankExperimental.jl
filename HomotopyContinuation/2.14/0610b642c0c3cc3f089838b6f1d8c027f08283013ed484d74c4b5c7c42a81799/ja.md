```
compose(G::Union{AbstractSystem,System}, F::Union{AbstractSystem,System})
```

合成 $G(F(x))$ を構築します。中置演算子 `∘` ( \circ と書かれます) を使用することもできます。

### 例

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
