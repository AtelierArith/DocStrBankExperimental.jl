```
eigenvaluesInGrid(
    m::AIMSteppingMethod,
    p::NumericAIMProblem{N,T},
    c::AIMCache{N,T},
    grid::Tuple{T,T};
    roots_atol::Real = 1.0e-10,
    roots_rtol::Real = 1.0e-10,
    roots_xatol::Real = 1.0e-10,
    roots_xrtol::Real = 1.0e-10,
    roots_maxevals::Int = 100
    ) where {N <: Unsigned, T <: Real}
```

実数データポイントの範囲を検索領域として使用して固有値を見つけることを試みます。収束設定の詳細については[Roots.jl](https://juliahub.com/docs/Roots/o0Xsi/1.0.7/reference/#Convergence)を参照してください。

# 入力

  * `m::AIMSteppingMethod`: 使用するステッピングメソッド。
  * `p::NumericAIMProblem{N,T}`: 以前に定義された問題データ。
  * `c::AIMCache{N,T}`: pから構築されたキャッシュ。
  * `grid::Tuple{T,T}`: (開始点, 終了点)からなるタプル。
  * `roots_atol::Real`: 絶対許容誤差。
  * `roots_rtol::Real`: 相対許容誤差。
  * `roots_xatol::Real`: 浮動小数点比較の絶対許容誤差。
  * `roots_xrtol::Real`: 浮動小数点比較の相対許容誤差。
  * `roots_maxevals::Int`: 実行されるアルゴリズムの反復回数。

# 出力

グリッド内で見つかった固有値を含む`Array{T,1}`型のオブジェクト。
