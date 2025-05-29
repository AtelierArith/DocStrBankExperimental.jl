```
spin_coherent(j::Real, θ::Real, ϕ::Real)
```

コヒーレントスピン状態を生成します（$|j, j\rangle$ 状態の回転）、すなわち

$$
|\theta, \phi \rangle = \hat{R}(\theta, \phi) |j, j\rangle
$$

ここで、回転演算子は次のように定義されます

$$
\hat{R}(\theta, \phi) = \exp \left( \frac{\theta}{2} (\hat{S}_- e^{i\phi} - \hat{S}_+ e^{-i\phi}) \right)
$$

および $\hat{S}_\pm$ はそれぞれプラスおよびマイナスのスピン-`j` 演算子です。

# 引数

  * `j::Real`: スピン量子数で、非負の整数または半整数であることができます
  * `θ::Real`: z軸からの回転角
  * `ϕ::Real`: x軸からの回転角

他に [`jmat`](@ref) および [`spin_state`](@ref) を参照してください。

# 参考文献

  * [Robert Jones, Spin Coherent States and Statistical Physics](https://web.mit.edu/8.334/www/grades/projects/projects19/JonesRobert.pdf)

```
