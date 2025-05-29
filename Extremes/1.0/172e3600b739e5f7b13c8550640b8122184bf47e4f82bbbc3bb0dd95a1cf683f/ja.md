```
fit(pd::Type{<:Gumbel}, y::Vector{<:Real}; method::String="mle")
```

データベクター `y` にGumbel分布をフィットさせます。

## 詳細

この関数は、同一分布のランダムサンプルからGumbel分布のパラメータを推定します。これは、Extremes.jlライブラリの軽量な機能です。

非定常性が存在する場合や高度な推論には、[`gevfit`](@ref) 関数がより適切です。

`method` 引数は、推定方法を選択するためのもので、`mle` は最尤推定、`pwm` は確率加重モーメント法を意味します。
