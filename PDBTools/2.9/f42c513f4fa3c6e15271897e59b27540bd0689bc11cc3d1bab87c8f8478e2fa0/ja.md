```
ContactMap{Bool|Real}
```

タンパク質構造内の残基間の接触マップを格納するデータ構造です。接触マップは、残基間の距離の行列です。接触は、残基の任意の2つの原子間の距離が指定された閾値 `dmax` よりも小さいと定義されます。

2つの残基間の距離が `dmax` より大きい場合、行列内の値は `missing` となり、残基間に接触がないことを示します。距離が `dmax` より小さい場合、行列内の値は残基間の距離になります。

`gap` パラメータは、指定された数の残基で分離された残基間の接触を計算するために使用されます。たとえば、`gap=3` の場合、接触マップは配列内で少なくとも3つの残基で分離された残基間で計算されます。

# フィールド

  * `matrix::Matrix{Union{Missing,T}}`: 残基間の距離の行列。
  * `d::T`: 接触のための閾値距離。
  * `gap::Int`: 接触を計算するための残基間のギャップ。

接触マップが `discrete=true` で計算された場合、行列には `Bool` 値が含まれ、`true` は接触を示し、`false` は接触がないことを示します。一方、`discrete=false` の場合、行列には残基間の距離が含まれます。
