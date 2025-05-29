```
`value(p::Mvp,:x₁=>v₁,:x₂=>v₂,...)`
 ̀(p::Mvp)(x₁=v₁,…,xₙ=vₙ)`
```

は、変数 `:x1` を `v1` に、`x2` を `v2` に同時に置き換えたときの `p` の値を返します。

```julia-repl
julia> p=-2+7x^5*inv(y)
Mvp{Int64}: 7x⁵y⁻¹-2

julia> p(x=2)
Mvp{Int64}: -2+224y⁻¹

julia> p(y=1)
Mvp{Int64}: 7x⁵-2

julia> p(x=2,y=1)
Mvp{Int64}: 222
```

最後の値が整数ではなく、定数 `Mvp` であることに注意する必要があります（整合性のため）。そのような定数を基底環に変換する方法については、関数 `scalar` を参照してください。

```julia-repl
julia> p(x=y)
Mvp{Int64}: 7y⁴-2

julia> p(x=y,y=x)
Mvp{Int64}: -2+7x⁻¹y⁵
```

Puiseux 多項式である `Mvp` を評価すると、`root` への呼び出しが発生する可能性があります。

```julia-repl
julia> p=x^(1//2)*y^(1//3)
Mvp{Int64,Rational{Int64}}: x½y⅓

julia> p(;x=y)
Mvp{Int64,Rational{Int64}}: y⅚

julia> p(;x=4)
Mvp{Int64,Rational{Int64}}: 2y⅓

julia> p(;y=2.0)
Mvp{Float64,Rational{Int64}}: 1.2599210498948732x½
```
