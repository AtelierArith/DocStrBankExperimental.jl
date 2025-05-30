```
t8_cmesh_trees_destroy(trees)
```

ツリー構造体に割り当てられたすべてのメモリを解放します。これは、すべての粗いツリーとゴースト、それらの面隣接エントリと属性、およびツリーの追加構造が解放されることを意味します。

# 引数

  * `trees`:[in,out] 解放されるツリー構造体。出力時にNULLに設定されます。

### プロトタイプ

```c
void t8_cmesh_trees_destroy (t8_cmesh_trees_t *trees);
```
