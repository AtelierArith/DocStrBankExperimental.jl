`induced_linear_form(W, H, h)`

このルーチンは、与えられた最大ランクの冪零部分群の冪零類を含む冪零群の Weyl 群 `W` の冪零類を見つけるために使用されます。この冪零部分群は、`W` の反射部分群 `H` によって表されます。

引数 `h` は、単純根に対する値によって与えられる `H` の根に対する線形形式です。この線形形式は、`H` の根の直交に対して `0` で `W` の根に拡張され、最終的に得られた形式は、単純根に対して正の値を取るように `W` の要素によって共役されます。初期の形式が `H` のためのダインキン-リチャードソン図を記述している場合、結果は `W` のためのダインキン-リチャードソン図を記述します。

```julia-repl
julia> W=coxgroup(:F,4)
F₄

julia> H=reflection_subgroup(W,[1,3])
F₄₍₁₃₎=A₁×Ã₁Φ₁²

julia> induced_linear_form(W,H,[2,2])
4-element Vector{Int64}:
 0
 1
 0
 0

julia> uc=UnipotentClasses(W);

julia> uc.classes[4].dynkin
4-element Vector{Int64}:
 0
 1
 0
 0

julia> uc.classes[4]
UnipotentClass(A₁+Ã₁)
```

上記の例は、タイプ `A₁×Ã₁` のレヴィ部分群の正則類を含む類が `A₁+Ã₁` であることを示しています。
