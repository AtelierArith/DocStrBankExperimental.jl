```
struct BlockSparsityPattern <: AbstractSparsityPattern
```

データ構造は、最終的な*ブロック*スパース行列の非ゼロエントリを表します。

ユーザー向けのドキュメントについては、コンストラクタ [`BlockSparsityPattern(::Vector{Int})`](@ref BlockSparsityPattern(::Vector{Int})) を参照してください。

# 構造体フィールド

  * `nrows::Int`: 行数
  * `ncols::Int`: 列数
  * `block_sizes::Vector{Int}`: 行および列のブロックサイズ
  * `blocks::Matrix{SparsityPattern}`: サイズ `length(block_sizes) × length(block_sizes)` の行列で、`blocks[i, j]` はブロック `(i, j)` に対応する [`SparsityPattern`](@ref) です。

!!! warning "内部構造体"
    この構造体の具体的な実装、例えば構造体フィールド、型レイアウト、型パラメータは内部的なものであり、依存すべきではありません。

