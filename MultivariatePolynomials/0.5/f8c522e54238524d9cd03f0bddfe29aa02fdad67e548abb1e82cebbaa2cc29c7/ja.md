```
monomials(p::AbstractPolynomialLike)
```

`p`の非ゼロ項のモノミアルに対するイテレータを返し、ポリノミアルを減少順にソートします。

```
monomials(vars::Union{Vector{<:AbstractVariable},Tuple}, degs::AbstractVector{Int}, filter::Function = m -> true)
```

変数`vars`を持つすべてのモノミアルベクトル`m`のベクトルを構築します。ここで、次数`degree(m)`が`degs`にあり、`filter(m)`が`true`である必要があります。

詳細は[`ExponentsIterator`](@ref)を参照してください。

### 例

$$
4x^2y + xy + 2x
$$

に対して`monomials`を呼び出すと、$[x^2y, xy, x]$のイテレータが返されるべきです。

`monomials((x, y), [1, 3], m -> degree(m, y) != 1)`を呼び出すと、`x^2*y`と`y`がフィルタによって除外され、`[x^3, x*y^2, y^3, x]`が返されるべきです。
