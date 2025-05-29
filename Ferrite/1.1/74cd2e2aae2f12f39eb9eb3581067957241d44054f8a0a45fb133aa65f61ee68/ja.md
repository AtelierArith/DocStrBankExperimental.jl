```
struct SparsityPattern <: AbstractSparsityPattern
```

最終的な疎行列における非ゼロエントリを表すデータ構造です。

ユーザー向けのドキュメントについては、コンストラクタ [`SparsityPattern(::Int, ::Int)`](@ref) を参照してください。

# 構造体フィールド

  * `nrows::Int`: 行数
  * `ncols::Int`: 列数
  * `rows::Vector{Vector{Int}}`: 長さ `nrows` のベクターで、`rows[i]` は行 `i` の非ゼロエントリの列インデックスの*ソートされた*ベクターです。

!!! warning "内部構造体"
    この構造体の具体的な実装、例えば構造体フィールド、型レイアウト、型パラメータは内部的なものであり、依存すべきではありません。

