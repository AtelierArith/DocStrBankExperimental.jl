```
computeEigenvalues(
    m::AIMSteppingMethod,
    p::QuadraticEigenvalueProblem{N,T},
    c::AIMCache{N,Polynomial{T}};
    plr_polish::Bool = true, 
    plr_epsilon::Real = convert(T, 1.0e-10)
    ) where {N <: Unsigned, T <: Number}
```

問題 `p` の固有値を対応するキャッシュ `c` と共に計算します。

# 入力

  * `m::AIMSteppingMethod`: 使用するステッピングメソッド。
  * `p::QuadraticEigenvalueProblem`: 以前に定義された問題データ。
  * `c::AIMCache`: p から構築されたキャッシュ。
  * `plr_polish::Bool`: PolynomialRoots に元の多項式を見つかった各根で割り、完全な多項式を使用して結果を磨くように指示します。
  * `plr_epsilon::Real`: Skowron & Gould 論文で説明されている停止基準。これは根が計算される精度ではありません。

# 出力

計算された固有値を含む `Array{T,1}` 型のオブジェクト。
