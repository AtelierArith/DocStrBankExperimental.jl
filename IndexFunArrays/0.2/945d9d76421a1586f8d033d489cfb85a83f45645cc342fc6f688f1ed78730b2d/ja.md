```
normal([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    sigma=1.0,
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

オフセットに位置するガウスピーク。 この正規分布（ガウス）は、その積分によって正規化されています。 最大値に正規化されたバージョンについては、`gaussian`を参照してください。

# 引数:

  * `sigma`: ガウスの（標準偏差）幅
  * `offset`: ガウスの中心位置。タプルまたはインジケーター `CtrCorner`、`CtrEnd`、`CtrFT`、`CtrRFT` などを使用できます。
  * `scale`: ピクセルのスケール。デフォルトでは `ScaUnit` が想定されています
  * `weight`: 結果の強度。リストモードをサポートします（ドキュメントについては rr2 を参照）
  * `accumulator`: リストモードデータを重ね合わせるために使用される方法。リストモードにのみ適用されます

```jldoctest
julia> normal((5,5))
5×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#107#109"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.00291502  0.0130642  0.0215393  0.0130642  0.00291502
 0.0130642   0.0585498  0.0965324  0.0585498  0.0130642
 0.0215393   0.0965324  0.159155   0.0965324  0.0215393
 0.0130642   0.0585498  0.0965324  0.0585498  0.0130642
 0.00291502  0.0130642  0.0215393  0.0130642  0.00291502

julia> sum(normal((5,5)))
 0.9818147610543744

julia> sum(normal((25,25)))
 1.000000010701151

julia> sum(normal((55,55), sigma=(5.0,2.0)))
0.9999999639340563
```

---

normal(arr::AbstractArray; offset=CtrFt, sigma=1.0, scaling=ScaUnit)

これは `normal(eltype(arr), size(arr), sigma=sigma, scaling=scaling, offset=offset)` のラッパーです。
