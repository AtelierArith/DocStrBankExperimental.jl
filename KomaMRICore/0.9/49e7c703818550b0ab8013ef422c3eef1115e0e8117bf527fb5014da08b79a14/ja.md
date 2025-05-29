```
spinor = Spinor(α, β)
```

Spinor(α, β) は、Cayley-Klein パラメータ α と β を持ちます。 "Introduction to the Shinnar-Le Roux algorithm" に基づいて、Patrick Le Roux (1995)。スピノールは 3D 回転を表現する方法であり、基礎となる表現は 2 X 2 の複素ユニタリ行列 ($\alpha,\beta\in\mathbb{C}$) です：

$$
R=\left[\begin{array}{cc}
\alpha & -\beta^{*}\\
\beta & \alpha^{*}
\end{array}\right],
$$

ここで $|\alpha|^2+|\beta|^2 = 1$ です。

この後、$(x,y,z)$ の $2\times2$ 表現に対して次のように作用します $V^{+} = R V R^{*}$。

# 引数

  * `α`: (`::Complex{Float64}`) Cayley-Klein パラメータ α
  * `β`: (`::Complex{Float64}`) Cayley-Klein パラメータ β

# 戻り値

  * `spinor`: (`::Spinor`) スピノール構造体
