```
fig = nicholsplot{T<:LTISystem}(systems::Vector{T}, w::AbstractVector; kwargs...)
```

`LTISystem`(s)のニコルスプロットを作成します。周波数ベクトル `w` をオプションで提供できます。

キーワード引数:

```
text = true
Gains = [12, 6, 3, 1, 0.5, -0.5, -1, -3, -6, -10, -20, -40, -60]
pInc = 30
sat = 0.4
val = 0.85
fontsize = 10
```

`pInc` は位相線の間の度数の増分を決定します。

`sat` ∈ [0,1] はゲイン線の飽和を決定します。

`val` ∈ [0,1] はゲイン線の明るさを決定します。

追加のキーワード引数はシステムをプロットする関数に送信され、通常の RecipesBase.jl 構文を使用して色、線スタイルなどを指定するために使用できます。

この関数は、二条項BSDライセンスの対象となるコードに基づいています。著作権 2011 Will Robertson 著作権 2011 Philipp Allgeuer
