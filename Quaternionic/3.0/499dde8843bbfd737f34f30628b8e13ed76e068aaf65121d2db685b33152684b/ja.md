```
∂log(Z::Rotor)
```

`log(Z)`の`Z`の成分に関する勾配を返します。

結果には「オフシェル」成分の勾配が含まれており、これは`Rotor`に対してノルムを変化させる方向に`Z`を変化させることは許可されていないにもかかわらず、その方向で勾配を測定することを意味します。つまり、返される四元数のベクトルの要素は次のようになります。

$$
\begin{aligned}
  \left[
    \frac{\partial} {\partial Z_w} \log(Z),
    \frac{\partial} {\partial Z_x} \log(Z),
    \frac{\partial} {\partial Z_y} \log(Z),
    \frac{\partial} {\partial Z_z} \log(Z)
  \right].
\end{aligned}
$$

`log(::Rotor)`は`QuatVec`であるにもかかわらず、導関数（したがって結果の各要素）は一般的な`Quaternion`です。

類似の関数については[`∂exp`](@ref)を、勾配とともに値を計算する関数については[`log∂log`](@ref)を参照してください。

# 例

```julia
julia> ∂log∂w, ∂log∂x, ∂log∂y, ∂log∂z = ∂log(randn(QuatVecF64));

```
