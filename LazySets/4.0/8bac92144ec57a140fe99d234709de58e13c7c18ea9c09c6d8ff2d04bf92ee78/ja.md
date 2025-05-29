# 拡張ヘルプ

```
σ(d::AbstractVector, B::AbstractBallp)
```

### アルゴリズム

$$
p
$$

-ノルムに沿った単位球のサポートベクトルは次のようになります：

$$
σ(d, \mathcal{B}_p^n(0, 1)) = \dfrac{\tilde{v}}{‖\tilde{v}‖_q},
$$

ここで、$\tilde{v}_i = \frac{|d_i|^q}{d_i}$（$d_i ≠ 0$ の場合）であり、そうでない場合は $\tilde{v}_i = 0$ です。すべての $i=1,…,n$ に対して、$q$ は $p$ の共役数です。アフィン変換 $x = r\tilde{x} + c$ によって、$\mathcal{B}_p^n(c, r)$ のサポートベクトルは次のようになります：

$$
σ(d, \mathcal{B}_p^n(c, r)) = \dfrac{v}{‖v‖_q},
$$

ここで、$v_i = c_i + r\frac{|d_i|^q}{d_i}$（$d_i ≠ 0$ の場合）であり、そうでない場合は $v_i = 0$ です。すべての $i = 1, …, n$ に対して。

方向のノルムがゼロの場合、球の中心が返されます。
