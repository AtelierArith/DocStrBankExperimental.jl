```
tsvd(A, nvals = 1; [maxiter, initvec, tolconv, tolreorth, debug])
```

演算子 `A` の切り捨てられた特異値分解 (TSVD) を Lanczos バイディアゴナリゼーションによって計算します。Lanczos ベクトルは、以下に記載されているように部分的に直交化されます。

R. M. Larsen, *Lanczos bidiagonalization with partial reorthogonalization*, Department of Computer Science, Aarhus University, Technical report, DAIMI PB-357, September 1998.

# 位置引数:

  * `A`: インプレース更新操作をサポートする任意のもの

```
mul!(y::AbstractVector, A, x::AbstractVector, α::Number, β::Number)
```

および

```
mul!(y::AbstractVector, A::Adjoint, x::AbstractVector, α::Number, β::Number)
```

は、`y := α*op(A)*x + β*y` という操作に対応し、ここで `op` は `A` の単位行列または共役転置のいずれかです。`initvec` 引数が提供されていない場合、さらに `A` が `eltype` と `size` をサポートする必要があります。

  * `nvals`: 計算する特異値とベクトルの数。デフォルトは1（最大のもの）。

# キーワード引数:

  * `maxiter`: Lanczos バイディアゴナリゼーションの最大反復回数。デフォルトは1000ですが、通常ははるかに少ない反復が必要です。
  * `initvec`: Lanczos プロセスの初期 `U` ベクトル。デフォルトはガウスのランダム変数のベクトルです。`initvec` の `length` と `eltype` は、`U` と `V` の基底ベクトルのサイズと要素の型を制御します。
  * `tolconv`: 特異値の相対収束基準。デフォルトは `sqrt(eps(real(eltype(A))))` です。
  * `tolreorth`: ω 再帰によって測定された Lanczos ベクトルの内積に対する絶対許容誤差。デフォルトは `sqrt(eps(real(eltype(initvec))))` です。`0.0` と `Inf` はそれぞれ完全な再直交化と再直交化なしに対応します。
  * `debug`: デバッグ情報を印刷するためのブールフラグ

# 出力:

プロセスの出力は三重タプル `(U, s, V)` です。

  * `U`: `size(A, 1)` 倍の `nvals` 行列の左特異ベクトル。
  * `s`: `A` の特異値の長さ `nvals` のベクトル。
  * `V`: `size(A, 2)` 倍の `nvals` 行列の右特異ベクトル。

# 例

```jldoctest
julia> A = matrixdepot("LPnetlib/lp_osa_30")
4350×104374 SparseArrays.SparseMatrixCSC{Float64, Int64} with 604488 stored entries:
⠙⠮⠷⠶⠽⠶⠽⠶⠮⠷⠮⠷⠶⠽⠶⠽⠶⠬⠷⠮⠷⠦⠽⠶⠽⠶⠽⠶⠮⠷⠮⠷⠶⠽⠶⠽⠶⠭⠷⠦

julia> U, s, V = tsvd(A, 5);

julia> round.(s, digits=7)
5-element Vector{Float64}:
 1365.8944098
 1033.2125634
  601.3524529
  554.107656
  506.0414587
```
