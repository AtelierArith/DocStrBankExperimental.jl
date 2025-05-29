```
∂exp(Z::QuatVec)
```

`exp(Z)`の`Z`の成分に関する勾配を返します。

結果には「オフシェル」成分の勾配が含まれており、`QuatVec`のスカラー成分は許可されていないにもかかわらず、その方向で勾配を測定します。つまり、返される四元数ベクトルの最初の要素は

$$
\begin{aligned}
  \left.\frac{\partial} {\partial Z_w} \exp(Z) \right|_{Z_w=0}.
\end{aligned}
$$

`exp(::QuatVec)`は`Rotor`であるにもかかわらず、導関数（したがって結果の各要素）は一般的な`Quaternion`であることに注意してください。

類似の関数については[`∂log`](@ref)を、勾配とともに値を計算する関数については[`exp∂exp`](@ref)を参照してください。

# 例

```julia
julia> ∂exp∂w, ∂exp∂x, ∂exp∂y, ∂exp∂z = ∂exp(randn(QuatVecF64));

```
