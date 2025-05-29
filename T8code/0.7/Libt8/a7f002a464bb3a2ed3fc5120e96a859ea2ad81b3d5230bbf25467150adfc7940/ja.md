```
t8_cmesh_set_join_by_stash(cmesh, connectivity, do_both_directions)
```

未コミットのcmeshの面接続情報をcmeshスタッシュに基づいて設定します。

!!! warning
    このルーチンは非常に大きなメッシュに対しては高コストになる可能性があります。この場合、完全な機能を持つメッシュジェネレーターの使用を検討してください。


!!! note
    このルーチンは周期境界を検出しません。


# 引数

  * `cmesh`:[in,out] 未コミットのcmesh。ツリーのeclassと頂点は設定する必要があります。
  * `connectivity`:[in,out] connectivityがNULLでない場合、変数は割り当てられた面接続配列へのポインタで埋められます。この配列の所有権は呼び出し元に移ります。この引数は主にデバッグおよびテスト目的で使用されます。*connectivity*の次元は[ntrees,[`T8_ECLASS_MAX_FACES`](@ref),3]です。各要素および各面について、次の情報が保存されます：neighbor*tree*id、neighbor*dual*face_id、orientation
  * `do_both_directions`:[in] 両方の隣接側から接続を計算します。計算にかかる時間が大幅に長くなります。

### プロトタイプ

```c
void t8_cmesh_set_join_by_stash (t8_cmesh_t cmesh, int **connectivity, const int do_both_directions);
```
