```
bound_perron_frobenius_eigenvalue(A, max_iter=10)
```

非負行列 `A` のペロン・フロベニウス固有値の上限を見つけます。

### 入力

  * `A` – 正方形の実非負行列
  * `max_iter` – ペロン・フロベニウス固有ベクトルの初期近似を計算するために内部で使用されるべきパワー法の最大反復回数

### 例

```julia-repl
julia> A = [1 2;3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> bound_perron_frobenius_eigenvalue(A)
5.372281323275249
```
