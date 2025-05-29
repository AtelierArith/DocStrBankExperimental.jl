```
t8_mesh_get_element_class(mesh, locid)
```

# 引数

  * `locid`:[in] ローカル番号は、ローカルに関連する任意の次元の点を指定できます。点は、t8*eclass*tの要素クラスに逆順で並べられています。ローカルインデックスはこの順序で累積されます。

### プロトタイプ

```c
t8_locidx_t t8_mesh_get_element_class (t8_mesh_t *mesh, t8_locidx_t locid);
```
