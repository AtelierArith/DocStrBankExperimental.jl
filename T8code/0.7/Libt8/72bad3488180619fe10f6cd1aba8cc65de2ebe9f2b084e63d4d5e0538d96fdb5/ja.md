```
t8_vec_tri_normal(p1, p2, p3, normal)
```

三つの頂点によって与えられた三角形の法線を計算します。

# 引数

  * `p1`:[in] 3Dベクトル。
  * `p2`:[in] 3Dベクトル。
  * `p3`:[in] 3Dベクトル。
  * `Normal`:[out] 三角形のベクトル。（必ずしも長さ1である必要はありません！）

### プロトタイプ

```c
static inline void t8_vec_tri_normal (const double p1[3], const double p2[3], const double p3[3], double normal[3]);
```
