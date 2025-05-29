```julia
nanbinmean(x, y, xedges::AbstractRange)
```

`NaN`を無視して、`x`軸に沿った`length(xedges)-1`の等間隔のビンに入る`y`値の加重平均を計算します。 

`x`データの配列は一次元配列（AbstractVectorの任意のサブタイプ）として与えられ、`y`は1次元または2次元配列（AbstractVecOrMatの任意のサブタイプ）として与えられます。`y`が2次元配列の場合、`y`の各列は別々の変数として扱われます。
