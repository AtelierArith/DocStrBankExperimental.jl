```
LC(d::Real=0.0)
```

拡張線形再結合操作を返します。詳細は[Recombination Interface](@ref)を参照してください。これは、子孫 `u` と `v` を次のように生成します。

  * $$
    u_i = x_i + \alpha (y_i - x_i)
    $$
  * $$
    v_i = y_i + \alpha (x_i - y_i)
    $$

ここで、$\alpha$ は区間 $[-d;d+1]$ で一様にランダムに選ばれます。
