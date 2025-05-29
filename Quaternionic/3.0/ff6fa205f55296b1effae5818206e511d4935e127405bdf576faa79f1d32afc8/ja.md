```
slerp∂slerp(q₁, q₂, τ)
```

`slerp`の値と勾配を返します。

勾配は各入力引数に対して順番に計算され、各クォータニオンは4つの引数の系列として扱われます。つまり、合計10個のクォータニオンが返されます：

$$
\begin{aligned}
  &\big[\\
    &\quad \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₁.w} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₁.x} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₁.y} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₁.z} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₂.w} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₂.x} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₂.y} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial q₂.z} \mathrm{slerp}(q₁, q₂, τ), \\
    &\quad \frac{\partial}{\partial \tau} \mathrm{slerp}(q₁, q₂, τ), \\
  &\big]
\end{aligned}
$$

便宜上、これは4タプルで、最初の要素が`slerp`、次に導関数の最初の4つの成分、次に次の4つの成分、最後に導関数の最後の成分が続きます。

値だけについては[`slerp`](@ref)を、`τ`に関する値と導関数だけについては[`slerp∂slerp∂τ`](@ref)を参照してください。

# 例

```julia
julia> (q1, q2), τ = randn(RotorF64, 2), rand();

julia> s, ∂s∂q₁, ∂s∂q₂, ∂s∂τ = slerp∂slerp(q₁, q₂, τ);

```
