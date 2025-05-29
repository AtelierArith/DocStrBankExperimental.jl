```
function ismv(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    r::Real = 2*maximum(vsz),
    tol::Real = 1e-3,
    maxit::Integer = 500,
    verbose::Bool = false,
) -> Tuple{typeof(similar(f)), typeof(similar(mask))}
```

反復球面平均値法 (iSMV) [1].

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: 展開された（マルチエコー）フィールド/位相
  * `mask::AbstractArray{Bool, 3}`: 興味領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: smvカーネルのボクセルサイズ

### キーワード

  * `r::Real = 2*maximum(vsz)`: `vsz`の単位でのsmvカーネルの半径
  * `tol::Real = 1e-3`: 停止許容値
  * `maxit::Integer = 500`: 最大反復回数
  * `verbose::Bool = false`: 収束情報を表示

### 戻り値

  * `typeof(similar(f))`: 背景補正された局所フィールド/位相
  * `typeof(similar(mask))`: 膨張されたバイナリマスク

### 参考文献

[1] Wen Y, Zhou D, Liu T, Spincemaille P, Wang Y. An iterative spherical mean     value method for background field removal in MRI.  Magnetic resonance in     medicine. 2014 Oct;72(4):1065-71.
