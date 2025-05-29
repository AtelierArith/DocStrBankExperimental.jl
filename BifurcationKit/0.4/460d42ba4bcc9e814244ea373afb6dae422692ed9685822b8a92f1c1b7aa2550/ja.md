```
多項式接線予測器
```

  * `n::Int64`: 多項式の次数
  * `k::Int64`: 多項式フィットに使用される最後の解ベクトルの長さ
  * `A::Matrix{T} where T<:Real`: 補間用の行列
  * `tangent::BifurcationKit.AbstractTangentComputation`: 多項式予測子が不可能な場合の接線アルゴリズム
  * `solutions::DataStructures.CircularBuffer`: 解のベクトル
  * `parameters::DataStructures.CircularBuffer{T} where T<:Real`: パラメータのベクトル
  * `arclengths::DataStructures.CircularBuffer{T} where T<:Real`: アーク長のベクトル
  * `coeffsSol::Vector`: 解のための多項式の係数
  * `coeffsPar::Vector{T} where T<:Real`: パラメータのための多項式の係数
  * `update::Bool`: 最後の点 (x, p) を追加して予測子を更新しますか？これは、多項式予測のみを使用するために無効にすることができます。これは、二分法を使用して分岐検出中に予測子が複数回呼び出されるときに便利です。

# コンストラクタ

```
Polynomial(pred, n, k, v0)

Polynomial(n, k, v0)
```

  * `n` 多項式の次数
  * `k` 多項式フィットに使用される最後の解ベクトルの長さ
  * `v0` 保存される解の例。これは接線の `eltype` を取得するためだけに使用されます。

次のように使用できます

```
PALC(tangent = Polynomial(Bordered(), 2, 6, rand(1)))
```
