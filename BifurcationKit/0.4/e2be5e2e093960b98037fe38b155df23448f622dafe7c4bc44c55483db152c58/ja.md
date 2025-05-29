```julia
struct EigKrylovKit{T, vectype} <: BifurcationKit.AbstractMFEigenSolver
```

`KrylovKit.jl`に基づく固有値ソルバーを作成します。

## フィールド

  * `dim::Int64`: Krylov次元 デフォルト: KrylovDefaults.krylovdim[]
  * `tol::Any`: 許容誤差 デフォルト: 0.0001
  * `restart::Int64`: 再起動の回数 デフォルト: 200
  * `maxiter::Int64`: 最大反復回数 デフォルト: KrylovDefaults.maxiter[]
  * `verbose::Int64`: 詳細度 ∈ {0, 1, 2} デフォルト: 0
  * `which::Symbol`: 探索する固有値 :LR (最大の実数), :LM, ... デフォルト: :LR
  * `issymmetric::Bool`: 線形写像が対称であるかどうか、T<:Realの場合のみ意味があります デフォルト: false
  * `ishermitian::Bool`: 線形写像がエルミートであるかどうか デフォルト: false
  * `x₀::Any`: Krylov反復に使用するベクトルの例 デフォルト: nothing

## コンストラクタ

上記のフィールドを渡すだけで、`EigKrylovKit(;dim=2)`のようにします。
