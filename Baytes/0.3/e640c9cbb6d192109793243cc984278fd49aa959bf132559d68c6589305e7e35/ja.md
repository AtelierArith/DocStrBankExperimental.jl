```julia
struct Trace{C<:Baytes.TraceSummary, A<:NamedTuple, B}
```

指定されたアルゴリズムのためのサンプリングチェーンと診断を含みます。

# フィールド

  * `val::Array{Vector{A}, 1} where A<:NamedTuple`: モデルサンプル ~ 対応するチェーンの出力ベクトル、イテレーションのための内部ベクトル
  * `diagnostics::Vector`: アルゴリズムの診断 ~ 対応するチェーンの出力ベクトル、イテレーションのための内部ベクトル
  * `summary::Baytes.TraceSummary`: ポストプロセッシングに使用されるトレースに関する情報。
