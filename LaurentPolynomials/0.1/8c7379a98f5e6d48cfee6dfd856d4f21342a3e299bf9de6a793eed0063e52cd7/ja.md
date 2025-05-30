`pseudodiv(a::Pol, b::Pol)`

`a`を`b`で擬似除算します。`d`が`b`の主係数である場合、`d^(degree(a)+1-degree(b))a=q*b+r`となる`(q,r)`を計算し、`degree(r)<degree(b)`を満たします。除算は行わないため、任意の環で動作します。真の多項式の場合（`a`または`b`の評価が負の場合はエラー）。

```julia-repl
julia> pseudodiv(q^2+1,2q+1)
(2q-1, 5)

julia> (2q+1)*(2q-1)+5
Pol{Int64}: 4q²+4
```

Knuth AOCP2 4.6.1 アルゴリズム Rを参照してください。
