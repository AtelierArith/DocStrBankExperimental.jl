```
fastcholesky!(input; fallback_gmw81=true, symmetrize_input=true, gmw81_tol=PositiveFactorizations.default_δ(input), symmetric_tol=1e-8)
```

入力行列 `input` のコレスキー分解をインプレースで計算します。この関数は `fastcholesky` のインプレースバージョンです。最初に入力行列が対称であるかどうかをチェックし、対称であれば、入力を `Hermitian` 行列でラップして組み込みのコレスキー分解を使用します。入力行列が対称でなく、`symmetrize_input=true` の場合、入力行列を対称化し、再帰的に再試行します。入力行列が対称でなく、正定値でなく、`fallback_gmw81=true` の場合、フォールバックとして `GMW81` アルゴリズムを使用します。それ以外の場合はエラーをスローします。

# キーワード引数

  * `fallback_gmw81::Bool=true`: true の場合、入力行列が正定値でない場合にフォールバックとして `GMW81` アルゴリズムを使用します。
  * `symmetrize_input::Bool=true`: true の場合、最初の試行が失敗した場合にコレスキー分解を再試行する前に入力行列を対称化します。
  * `gmw81_tol::Real=PositiveFactorizations.default_δ(input)`: `GMW81` アルゴリズムのための入力行列の正定値性に関する許容誤差。
  * `symmetric_tol::Real=1e-8`: 入力行列の対称性に関する許容誤差。

!!! note
    入力行列がほぼ正定値であると予想される場合にのみ、この関数を使用してください。


```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> C = fastcholesky!([ 1.0 0.5; 0.5 1.0 ]);

julia> C.L * C.L' ≈ [ 1.0 0.5; 0.5 1.0 ]
true
```
