```
t8_stash_add_facejoin(stash, gid1, gid2, face1, face2, orientation)
```

スタッシュに面接続を追加します。

# 引数

  * `stash`:[in,out] 更新されるスタッシュ。
  * `id1`:[in] 最初の木のグローバルID。
  * `id2`:[in] 2番目の木のグローバルID。
  * `face1`:[in] 最初の木の面の番号。
  * `face2`:[in] 2番目の木の面の番号。
  * `orientation`:[in] 面同士の向き。

### プロトタイプ

```c
void t8_stash_add_facejoin (t8_stash_t stash, t8_gloidx_t gid1, t8_gloidx_t gid2, int face1, int face2, int orientation);
```
