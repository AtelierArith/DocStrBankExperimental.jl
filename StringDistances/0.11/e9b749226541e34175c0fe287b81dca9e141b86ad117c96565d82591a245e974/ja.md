TokenMax(dist)

`TokenMax{dist}`距離を作成します。これはAbstractStringsのみに定義されています。

`TokenMax{dist}`は距離`dist`を正規化し、距離、[`Partial`](@ref)修飾子、[`TokenSort`](@ref)修飾子、および[`TokenSet`](@ref)修飾子の最小値を返します。文字列の長さに依存するペナルティ項があります。

### 例

```julia-repl
julia> s1 = "New York Mets vs Atlanta"
julia> s2 = "Atlanta Braves vs New York Mets"
julia> evaluate(TokenMax(RatcliffObershelp()), s1, s2)
0.05
```
