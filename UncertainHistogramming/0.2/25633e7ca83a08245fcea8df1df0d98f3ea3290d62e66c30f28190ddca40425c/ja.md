```
UniformHistogram{T <: Number} <: ContinuousHistogram
```

各値-誤差ペアに対して一様カーネルを持つ[`ContinuousHistogram`](@ref)。

この[`ContinuousHistogram`]は、各$(x_i, \epsilon_i)$に対して一様カーネルを合計することによって形成されます。

$$
\mathcal{H}(y) = \frac{1}{M} \sum_{i = 1}^M \mathcal{U}(y; x_i, \epsilon_i),
$$

ここで

$$
\mathcal{U}(y; x_i, \epsilon_i) = \begin{cases}
\frac{1}{2\epsilon_i}, & y \in (x_i - \epsilon_i, x_i + \epsilon_i)
\\
0, & \mathrm{それ以外}
\end{cases}.
$$

これらの表現により、非中心の[`moment`](@ref)の計算が個々の非中心[`moment`](@ref)の単純な平均になります。

# 目次

  * `moments::Vector{T}`: `UniformHistogram`のためのモーメントのコレクションで、*オンライン*方式で更新されます
  * `values::Vector{T}`: `UniformHistogram`を[`construct`](@ref)するために使用される値
  * `errors::Vector{T}`: `UniformHistogram`を[`construct`](@ref)するために使用される誤差

!!! note
    統計は[`moment`](@ref)に関する計算から得られます。`values`と`errors`は視覚化の目的で必ず保存されます。

