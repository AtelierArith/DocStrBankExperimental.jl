```
exp_ikx([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    shift_by=size.÷2
    dims=ntuple(+, N),
    scale=ScaFT,
    weight=1,
    accumulator=sum)
```

`exp(-2pi i <k,x>)` に従った複素数値の位相ランプ。フーリエ空間で乗算因子として適用されると、実空間で `x` ピクセルのシフトを引き起こします。この効果は実際にはスケーリングパラメータの変更によって実現されることに注意してください。デフォルトのシフトは `size.÷2` で、これは `CtrFT` に対応しますが、`shift_by` に対して Ctr... 引数は使用できません。

引数 `shift_by` はリストモードをサポートしており、これを使用することで複数のシフトを同時に便利に実行できます。以下の最終例を参照してください。これはランダム化されたサブピクセル位置でデルタピークを生成します。

# 引数:

  * `offset`: ガウスの中心位置。タプルまたはインジケーター `CtrCorner`, `CtrEnd`, `CtrFT`, `CtrRFT` などを使用できます。
  * `shift_by`: 実空間でのシフト量。
  * `scale`: ピクセルのスケール。デフォルトでは `ScaUnit` が仮定されます。
  * `dims`: この関数を適用する次元。
  * `weight`: 結果の強度。リストモードをサポートします（ドキュメントは rr2 を参照）。
  * `accumulator`: リストモードデータを重ね合わせるために使用される方法。リストモードでのみ適用されます。

```jldoctest
julia> a = rr((4,3),offset=CtrCorner)
4×3 IndexFunArray{Float64, 2, IndexFunArrays.var"#37#39"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 0.0  1.0      2.0
 1.0  1.41421  2.23607
 2.0  2.23607  2.82843
 3.0  3.16228  3.60555

julia> using FourierTools; real(iffts(ffts(a).*exp_ikx(a, shift_by=(2.0,1.0))))
4×3 Matrix{Float64}:
 2.82843   2.0          2.23607
 3.60555   3.0          3.16228
 2.0      -2.22045e-16  1.0
 2.23607   1.0          1.41421

 julia> using FourierTools; y = real(ift(exp_ikx((101,101),weight=rand(60), shift_by=101.0 .*rand(2,60))));

```

---

```
exp_ikx(arr::AbstractArray; offset=CtrFt, shift_by==size(arr).÷2, scaling=ScaUnit)
```

これは `exp_ikx(eltype(arr), size(arr), shift_by=shift_by, scaling=scaling, offset=offset)` のラッパーです。
