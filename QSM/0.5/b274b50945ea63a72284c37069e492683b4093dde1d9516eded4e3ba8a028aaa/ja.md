```
pdf(
    f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)},
    mask::AbstractArray{Bool, 3},
    vsz::NTuple{3, Real};
    W::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing,
    pad::NTuple{3, Integer} = (0, 0, 0),
    bdir::NTuple{3, Real} = (0, 0, 1),
    Dkernel::Symbol = :i,
    lambda::Real = 0,
    tol::Real = 1e-5,
    maxit::Integer = ceil(sqrt(numel(mask))),
    verbose::Bool = false
) -> typeof(similar(f))
```

双極子場への射影 (PDF) [1].

### 引数

  * `f::AbstractArray{<:AbstractFloat, N ∈ (3, 4)}`: 展開された (マルチエコー) フィールド/位相
  * `mask::AbstractArray{Bool, 3}`: 興味領域のバイナリマスク
  * `vsz::NTuple{3, Real}`: 双極子カーネルのボクセルサイズ

### キーワード

  * `W::Union{Nothing, AbstractArray{<:AbstractFloat, M ∈ (3, N)}} = nothing`: データ忠実度重み
  * `pad::NTuple{3, Integer} = (0, 0, 0)`: ゼロパディング配列

      * `< 0`: パディングなし
      * `≥ 0`: 高速FFTサイズへの最小パディング
  * `bdir::NTuple{3, Real} = (0, 0, 1)`: Bフィールド方向の単位ベクトル
  * `Dkernel::Symbol = :i`: 双極子カーネル法
  * `lambda::Real = 0`: 正則化パラメータ
  * `tol::Real = 1e-5`: 反復ソルバーの停止許容誤差
  * `maxit::Integer = ceil(sqrt(length(mask)))`: 反復ソルバーの最大反復回数
  * `verbose::Bool = false`: 収束情報を表示

### 戻り値

  * `typeof(similar(f))`: 背景補正された局所フィールド/位相

### 参考文献

[1] Liu T, Khalidov I, de Rochefort L, Spincemaille P, Liu J, Tsiouris AJ, Wang Y. MRIのための双極子場への射影を用いた新しい背景場除去法。NMR in Biomedicine. 2011年11月;24(9):1129-36.
