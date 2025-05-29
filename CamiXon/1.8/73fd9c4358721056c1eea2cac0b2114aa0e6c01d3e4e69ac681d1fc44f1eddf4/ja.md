```
latent_heat_vaporization(atomicnumber::Int, temp::Real)
latent_heat_vaporization(element::String, temp:Real)
```

与えられた `element` の蒸発潜熱 *L*(*T*) (ジュール/K) は、温度 *T* (K) に対して、

$$
L(T) = -(B +C\cdot T \mathrm{log_{10}}T+D\cdot T^2/1000),
$$

ここで A,B,C,D は [`CamiXon.dictAntoineCoefficient`](@ref) に収集されたアントワネット係数です。

#### 例:

```
julia> latent_heat_vaporization("Li", 623.0)
-18473.64020109123
```
