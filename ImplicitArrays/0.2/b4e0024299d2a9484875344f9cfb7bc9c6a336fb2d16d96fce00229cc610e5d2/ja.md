```
BlockMatrix{T} <: AbstractArray{T, 2}
```

要素の型 `T` を持つ同じサイズの行列の暗黙的ブロック行列。

# コンストラクタ

```
BlockMatrix(blocks)
BlockMatrix{T}(blocks)
BlockMatrix{T}(rows, cols[, blocks...])
BlockMatrix(rows, cols, first_block[, more_blocks...])
```

与えられた行列の行列から新しいブロック行列を作成します。あるいは、`rows` と `cols` の数を指定して、行列のシーケンスからブロック行列を作成します。

# 例

```jldoctest; setup = :(using ImplicitArrays)
julia> A = [1 2; 3 4]; B = zeros(Int, 2, 2);

julia> C = [x * y for x in 2:3, y in 3:4];

julia> BlockMatrix(1, 4, A, B, B, C)
2×8 BlockMatrix{Int64}:
 1  2  0  0  0  0  6   8
 3  4  0  0  0  0  9  12
```

!!! note
    この型は高性能な目的には適していません。行列ブロックは任意の行列型の構成を可能にするために抽象コンテナに格納されます。詳細については、公式のJuliaドキュメントの[パフォーマンスのヒント](https://docs.julialang.org/en/v1/manual/performance-tips/)を参照してください。

