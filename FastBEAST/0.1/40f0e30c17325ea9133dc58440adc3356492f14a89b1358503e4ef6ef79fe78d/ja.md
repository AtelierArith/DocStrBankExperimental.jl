```
function allocate_aca_memory(
    ::Type{K}, maxrows::I, maxcolumns::I; maxrank=40
) where {I, K}
```

ACAのためのストレージの事前割り当て。

# 引数

  * `::Type{K}`: 行列のエントリの型。
  * `maxrows::I`: 行数。
  * `maxcolumns::I`: 列数。

# オプション引数

  * `maxrank=40`: ACAの最大ランク。近似に使用される行/列が増えると、ACAは停止します。
