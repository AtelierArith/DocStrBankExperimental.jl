```
AbstractShallowWaterEquations{NDIMS, NVARS}
```

古典的浅水方程をサブシステムとして含むすべての方程式系の抽象スーパタイプ、例えば、[`BBMBBMEquations1D`](@ref)、[`SvaerdKalischEquations1D`](@ref)、および[`SerreGreenNaghdiEquations1D`](@ref)です。1次元では、平坦な水深を持つ浅水方程式は次のように表されます。

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t + \frac{1}{2} g (h^2)_x + \frac{1}{2} h (v^2)_x &= 0,
\end{aligned}
$$

ここで、$h$は[`waterheight`](@ref)、$v$は[`velocity`](@ref)、$g$は[`gravity`](@ref)です。
