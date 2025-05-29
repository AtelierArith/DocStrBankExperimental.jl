```
undef_blocks
```

`UndefBlocksInitializer()`のエイリアスで、ブロック配列の初期化に使用されるシングルトン型[`UndefBlocksInitializer`](@ref)のインスタンスを構築します。これは、配列コンストラクタ呼び出し元が初期化されていないブロック配列を希望していることを示します。

# 例

```jldoctest
julia> BlockArray(undef_blocks, Matrix{Float32}, [1,2], [3,2])
2×2-blocked 3×5 BlockMatrix{Float32}:
 #undef  #undef  #undef  │  #undef  #undef
 ────────────────────────┼────────────────
 #undef  #undef  #undef  │  #undef  #undef
 #undef  #undef  #undef  │  #undef  #undef
```
