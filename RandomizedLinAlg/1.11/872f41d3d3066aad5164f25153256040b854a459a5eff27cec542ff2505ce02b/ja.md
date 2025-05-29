```
rsvd_fnkz(A, k)
```

ランダムに選択された列/行からの反復的な洗練によってランダム化SVDを計算します [^Friedland2006]。

# 引数

  * `A`: SVDを求める行列;
  * `k::Int`: 近似の希望ランク (`k ≤ min(m, n)`).

## キーワード

  * `l::Int = k`: 各反復でサンプリングする列/行の数 (`1 ≤ l ≤ k`);
  * `N::Int = minimum(size(A))`: 最大反復回数;
  * `ϵ::Real = prod(size(A))*eps()`: 収束のための相対閾値、スペクトルノルムの成長によって測定される;
  * `method::Symbol = :eig`: 解決すべき問題。

    1. `:eig`: 固有値問題。
    2. `:svd`: 特異値問題。
  * `verbose::Bool = false`: 各反復で収束情報を印刷します。

# 戻り値

`rank ≤ k` のSVDオブジェクト。

[^Friedland2006]: Friedland, Shmuel, et al. "Fast Monte-Carlo low rank approximations for matrices." System of Systems Engineering, 2006 IEEE/SMC International Conference on. IEEE, 2006.
