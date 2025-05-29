```
t8_cmesh_trees_get_ghost_face_neighbor_ext(ghost, face, ttf)
```

粗いゴーストと面番号を指定すると、隣接する木のローカルIDとその木から面への情報を返します。

# 引数

  * `ghost`:[in] 粗いゴースト。
  * `face`:[in] 面番号。
  * `ttf`:[out] NULLでない場合、この面の木から面への値で埋められます。

# 戻り値

隣接する木のグローバルID。

### プロトタイプ

```c
t8_gloidx_t t8_cmesh_trees_get_ghost_face_neighbor_ext (const t8_cghost_t ghost, const int face, int8_t *ttf);
```
