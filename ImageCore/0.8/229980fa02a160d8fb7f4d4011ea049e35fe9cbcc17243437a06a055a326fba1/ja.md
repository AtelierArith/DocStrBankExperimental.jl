```
takemap(f, A) -> fnew
takemap(f, T, A) -> fnew
```

値マッピング関数 `f` と配列 `A` が与えられたとき、"具体的な" マッピング関数 `fnew` を返します。`A` の要素に適用されると、`fnew` はストレージや表示のための有効な値を返すべきであり、例えば0から1の範囲（グレースケールの場合）や有効な色素の範囲です。`fnew` は `A` に存在する実際の値に適応される可能性があり、`A` にない入力に対して有効な値を生成しない場合があります。

オプションで、`fnew` が生成すべき出力タイプ `T` を指定することができます。

# 例:

```julia
julia> A = [0, 1, 1000];

julia> f = takemap(scaleminmax, A)
(::#7) (generic function with 1 method)

julia> f.(A)
3-element Array{Float64,1}:
 0.0
 0.001
 1.0
```
