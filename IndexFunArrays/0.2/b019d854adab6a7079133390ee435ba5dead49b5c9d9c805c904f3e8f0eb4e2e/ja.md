```
gaussian([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    sigma=1.0,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

オフセットに位置するガウスピーク。ガウスはその積分によって正規化されていないことに注意してください。最大値によって正規化されています。正規化された積分を持つバージョンについては、`normal`を参照してください。引数sigmaに対してもリストモードがサポートされています。以下の最終例では、ランダムな位置にランダムな強度と幅で60のガウスを生成します。

# 引数:

  * `sigma`: ガウスの（標準偏差）幅。タプルが供給されると、各エントリは対応する次元に沿った幅として解釈されます。
  * `offset`: ガウスの中心位置。タプルまたはインジケーター`CtrCorner`、`CtrEnd`、`CtrFT`、`CtrRFT`などを使用できます。
  * `scale`: ピクセルのスケール。デフォルトでは`ScaUnit`が想定されます。
  * `dims`: この関数を適用する次元。
  * `weight`: 結果の強度。リストモードをサポートしています（ドキュメントについてはrr2を参照）。
  * `accumulator`: リストモードデータを重ね合わせるために使用される方法。リストモードにのみ適用されます。

```jldoctest
julia> gaussian((5,5))
5×5 IndexFunArray{Float64, 2, IndexFunArrays.var"#100#102"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.0183156  0.082085  0.135335  0.082085  0.0183156
 0.082085   0.367879  0.606531  0.367879  0.082085
 0.135335   0.606531  1.0       0.606531  0.135335
 0.082085   0.367879  0.606531  0.367879  0.082085
 0.0183156  0.082085  0.135335  0.082085  0.0183156

julia> gaussian((6,6), sigma=5.0)
 6×6 IndexFunArray{Float64, 2, IndexFunArrays.var"#100#102"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
  0.165299  0.272532  0.367879  0.40657   0.367879  0.272532
  0.272532  0.449329  0.606531  0.67032   0.606531  0.449329
  0.367879  0.606531  0.818731  0.904837  0.818731  0.606531
  0.40657   0.67032   0.904837  1.0       0.904837  0.67032
  0.367879  0.606531  0.818731  0.904837  0.818731  0.606531
  0.272532  0.449329  0.606531  0.67032   0.606531  0.449329

julia> gaussian(Float32,(5,5),offset=CtrCorner)
  5×5 IndexFunArray{Float32, 2, IndexFunArrays.var"#100#102"{Float32, Tuple{Float64, Float64}, Tuple{Float32, Float32}}}:
   1.0          0.606531     0.135335    0.011109    0.000335463
   0.606531     0.367879     0.082085    0.00673795  0.000203468
   0.135335     0.082085     0.0183156   0.00150344  4.53999f-5
   0.011109     0.00673795   0.00150344  0.00012341  3.72665f-6
   0.000335463  0.000203468  4.53999f-5  3.72665f-6  1.12535f-7

julia> y = gaussian((100,100),offset = (100,100) .* rand(2,60), weight=rand(60), sigma=2.0 .*(0.3 .+rand(2,60)));

```

---

gaussian(arr::AbstractArray; offset=CtrFt, sigma=1.0, scaling=ScaUnit)

これは`gaussian(eltype(arr), size(arr), sigma=sigma, scaling=scaling, offset=offset)`のラッパーです。
