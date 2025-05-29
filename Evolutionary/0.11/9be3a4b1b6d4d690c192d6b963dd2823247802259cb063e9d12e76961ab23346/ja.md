```
IC(d::Real=0.0)
```

拡張中間再結合操作を返します。詳細は[Recombination Interface](@ref)を参照してください。これは、子孫 `u` と `v` を次のように生成します。

  * $$
    u_i = x_i + \alpha_i (y_i - x_i)
    $$
  * $$
    v_i = y_i + \alpha_i (x_i - y_i)
    $$

ここで、$\alpha_i$ は区間 $[-d;d+1]$ で一様にランダムに選ばれます。
