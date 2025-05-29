```
struct QuEraTaskSpecification <: QuEraSchema
```

マシンのタスクのスキーマ表現。

[`to_schema`](@ref) および [`to_schema_no_validation`](@ref) の出力と、[`execute(task::QuEraTaskSpecification)`](@ref) への入力です。

# フィールド

  * `nshots::Int`: ショットの数（ハミルトニアンが実行される回数）
  * `lattice::Lattice`: ブラベー格子ベクトルとサイト
  * `effective_hamiltonian::EffectiveHamiltonian`: `RydbergHamiltonian` インスタンスをラップした `EffectiveHamiltonian`
