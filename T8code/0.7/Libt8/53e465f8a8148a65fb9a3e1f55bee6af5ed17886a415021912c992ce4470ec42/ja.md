```
t8_eclass_count_boundary(theclass, min_dim, per_eclass)
```

要素クラスと境界点のカウントを照会します。

# 引数

  * `theclass`:[in] この要素クラスの点を照会します。
  * `min_dim`:[in] より小さい次元の境界点を無視します。無視された点はカウント値が0になります。
  * `per_eclass`:[out] 各要素クラスごとにカウントされた境界オブジェクトのカウントで埋められる長さ T8*ECLASS*COUNT の配列。

# 戻り値

すべての境界点のカウント。

### プロトタイプ

```c
int t8_eclass_count_boundary (t8_eclass_t theclass, int min_dim, int *per_eclass);
```
