```
attractiveness(sindex::AttractivenessSpatIndex{T}, enu::ENU; aggregator::Function=sum, calculate_attractiveness::Function=calculate_attractiveness, distance::Function=OpenStreetMapX.distance, explain::Bool=false) where T <: AbstractMetaPOI
```

指定された空間インデックス `sindex` と `enu` 座標に対する多次元の魅力測定値を返します。`enu` 座標は *必ず* `sindex.refLLA` を基準点として使用する必要があります。したがって、`enu` 座標は例えば `ENU(lla,sindex.refLLA)` を使用して計算する必要があります。`aggregator` 関数は魅力値を集約するために使用されます。集約は、魅力範囲内に複数の興味ポイントが存在する可能性があるため、必要です。関数 `calculate_attractiveness(a::T, poidistance::Number)` は、メタデータと距離に基づいて魅力を計算するために使用されます。距離関数 `distance(a::ENU, b::ENU)` は、ポイントペア間の距離を計算するために使用されます。

`explain` が true に設定されている場合、結果には魅力を計算するために使用された POI に関する詳細も含まれます。
