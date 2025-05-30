```
t8_cmesh_set_dimension(cmesh, dim)
```

cmeshの次元を設定します。もし[`t8_cmesh_set_tree_class`](@ref)を介してcmeshにツリーが挿入された場合、その次元は挿入されたツリーの次元に自動的に設定されます。しかし、cmeshが分割された状態で構築され、このプロセスの部分が空である場合は、手動で次元を設定する必要があります。

# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `dim`:[in] 設定する次元。0 <= dim <= 3を満たす必要があります。この関数を呼び出す前にcmeshはコミットされていない必要があります。

### プロトタイプ

```c
void t8_cmesh_set_dimension (t8_cmesh_t cmesh, int dim);
```
