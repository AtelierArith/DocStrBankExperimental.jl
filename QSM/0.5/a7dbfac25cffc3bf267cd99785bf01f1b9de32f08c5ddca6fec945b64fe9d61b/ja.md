```
lbv(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    atol::Real = sqrt(eps(Float64)),
    rtol::Real = sqrt(eps(Float64)),
    maxit::Integer = maximum(size(f)),
    verbose::Bool = false
) -> typeof(similar(f))
```

ラプラス境界値問題 (LBV) [1].

ラプラス演算子は、二次中心有限差分を使用して計算されます。得られたポアソン方程式は、均質ディリクレ境界条件 (BC) を持つ ROI (`mask`) 内で解かれ、多重格子前処理共役勾配法を使用します。ROI の境界は、外部の値 (`mask = 0`) が境界点として、内部の値 (`mask = 1`) が内部点として扱われるように設定されます。すなわち、BC: `fl[!mask] = 0`。

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: 展開された (マルチエコー) フィールド/位相
  * `mask::AbstractArray{Bool, 3}`: 興味のある領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: ボクセルサイズ

### キーワード

  * `atol::Real = sqrt(eps(Float64))`: 絶対停止許容誤差
  * `rtol::Real = sqrt(eps(Float64))`: 相対停止許容誤差
  * `maxit::Integer = maximum(size(f))`: cg 反復の最大数
  * `verbose::Bool = false`: 収束情報を表示

### 戻り値

  * `typeof(similar(f))`: 背景補正された局所フィールド/位相

### 参考文献

[1] Zhou D, Liu T, Spincemaille P, Wang Y. 背景フィールド除去のためのラプラス境界値問題の解法. NMR in Biomedicine. 2014年3月;27(3):312-9.
