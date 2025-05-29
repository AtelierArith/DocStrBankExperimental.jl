```
isapprox(df1::AbstractDataFrame, df2::AbstractDataFrame;
         rtol::Real=atol>0 ? 0 : √eps, atol::Real=0,
         nans::Bool=false, norm::Function=norm)
```

不正確な等価比較。`df1` と `df2` は同じサイズと列名を持っている必要があります。`isapprox` が与えられたキーワード引数を使用して `df1` と `df2` に格納されたすべての列のペアに適用されると `true` を返す場合、`true` を返します。
