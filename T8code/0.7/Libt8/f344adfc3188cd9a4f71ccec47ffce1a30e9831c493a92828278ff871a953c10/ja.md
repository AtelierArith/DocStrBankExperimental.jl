```
t8_cmesh_trees_copy_part(trees_dest, part_dest, trees_src, part_src)
```

ツリー配列をあるパートから別のパートにコピーします。

# 引数

  * `trees_dest`:[in,out] 目的地パートのツリー構造体。
  * `part_dest`:[in] 目的地パートのインデックス。t8*cmesh*trees*start*partによって初期化されている必要があり、alloc = 0でなければなりません。
  * `trees_src`:[in] ソースパートのツリー構造体。
  * `part_src`:[in] 目的地パートのインデックス。これは有効なパートでなければならず、t8*cmesh*trees*finish*partが呼び出されている必要があります。

### プロトタイプ

```c
void t8_cmesh_trees_copy_part (t8_cmesh_trees_t trees_dest, int part_dest, t8_cmesh_trees_t trees_src, int part_src);
```
