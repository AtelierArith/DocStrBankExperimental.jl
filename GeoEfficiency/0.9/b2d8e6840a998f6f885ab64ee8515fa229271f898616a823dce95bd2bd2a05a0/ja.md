```
batch(
	detector::Detector,
	srcHeights_array::Vector{S},
	srcRhos_array::Vector{S}=[0.0],
	srcRadii_array::Vector{S}=[0.0],
	srcLengths_array::Vector{S}=[0.0],
	ispoint::Bool=true
	)::String 	where S <: Real
```

検出器 `detector` の `geometrical efficiency` のバッチ計算を提供します。結果は検出器の名前を付けた **`CSV`** ファイルに保存されます。デフォルトでは、この **`CSV`** ファイルは **`/home/terasaki/GeoEfficiency/results`** にあります。このメソッドは **`CSV`** ファイルへの実際のパスを返します。また、結果のログがコンソールに表示されます。

  * `srcHeights_array`: バッチに供給するソースの高さのリスト。
  * `srcRhos_array`: バッチに供給するソースのオフ軸距離のリスト。
  * `srcRadii_array`: バッチに供給するソースの半径のリスト。
  * `srcLengths_array`: バッチに供給するソースの長さのリスト。

ソースのセットは、`srcRhos_array`、`srcRadii_array`、および `srcLengths_array` 配列のすべての有効な **組み合わせ** を `ispoint` と組み合わせて構築されます。

!!! warning
      * `ispoint` が `true` の場合、ソースのタイプは点ソースであり、`srcRadii_array` および `srcLengths_array` 配列のパラメータは完全に無視されます。
      * `ispoint` が `false` の場合、`srcRhos_array` のパラメータは完全に無視されます。

