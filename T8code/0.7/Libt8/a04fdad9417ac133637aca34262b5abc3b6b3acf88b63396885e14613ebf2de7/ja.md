```
t8_mat_init_yrot(mat, angle)
```

与えられた3x3行列を、指定された角度でy軸周りの回転行列として初期化します。

# 引数

  * `mat`:[in,out] 3x3行列。
  * `angle`:[in] ラジアンでの回転角。

### プロトタイプ

```c
static inline void t8_mat_init_yrot (double mat[3][3], const double angle);
```
