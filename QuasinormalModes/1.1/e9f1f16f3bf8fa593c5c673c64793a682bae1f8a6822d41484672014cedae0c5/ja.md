```
eigenvaluesInGrid(
    m::AIMSteppingMethod,
    p::NumericAIMProblem{N,T},
    c::AIMCache{N,T},
    grid::Tuple{T,T,Int64,Int64};
    xtol::Real = 1.0e-10,
    ftol::Real = 1.0e-10,
    iterations::Int = 1000
    ) where {N <: Unsigned, T <: Complex}
```

複素平面データポイントのグリッドを使用して固有値を見つけることを試みます。これは、nlsolveに渡される初期推定値です。

# 入力

  * `m::AIMSteppingMethod`: 使用するステッピングメソッド。
  * `p::NumericAIMProblem{N,T}`: 以前に定義された問題データ。
  * `c::AIMCache{N,T}`: pから構築されたキャッシュ。
  * `grid::Tuple{T,T,Int64,Int64}`: (開始点、終了点、実数点の数、虚数点の数)からなるタプル。
  * `xtol::Real`: 収束が宣言される2つの連続した反復間のxのノルム差。
  * `ftol::Real`: 収束が宣言される残差の無限ノルム。
  * `iterations::Int`: NLsolveによって実行される最大反復回数。

# 出力

グリッド内で見つかったモードを含む`Array{T,1}`型のオブジェクト。
