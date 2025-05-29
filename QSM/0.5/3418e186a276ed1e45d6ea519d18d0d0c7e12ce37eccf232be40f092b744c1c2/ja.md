```
vsharp(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    r::AbstractVector{<:Real} = 18*minimum(vsz):-2*maximum(vsz):2*maximum(vsz),
    thr::Real = 0.05,
) -> Tuple{typeof(similar(f)), typeof(similar(mask))}
```

位相データのための変数カーネル洗練された調和アーティファクト除去 (V-SHARP) [1].

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: アンワップされた (マルチエコー) フィールド/位相
  * `mask::AbstractArray{Bool, 3}`: 興味領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: smv カーネルのボクセルサイズ

### キーワード

  * `r::AbstractVector{<:Real} = 18*minimum(vsz):-2*maximum(vsz):2*maximum(vsz)`:   smv カーネルの半径 (mm)
  * `thr::Real = 0.05`: ハイパスフィルターの閾値

### 戻り値

  * `typeof(similar(f))`: 背景補正されたローカルフィールド/位相
  * `typeof(similar(mask))`: 膨張されたバイナリマスク

### 参考文献

[1] Wu B, Li W, Guidon A, Liu C. Whole brain susceptibility mapping using     compressed sensing. Magnetic resonance in medicine. 2012 Jan;67(1):137-47.
