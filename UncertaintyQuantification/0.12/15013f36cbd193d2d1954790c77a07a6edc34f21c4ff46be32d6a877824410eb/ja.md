```
EmpiricalPSD(ω::AbstractVector{<:Real}, p::AbstractVector{<:Real}) -> EmpiricalPSD
```

与えられた角周波数と手動で提供されたパワースペクトル密度値を使用して、`EmpiricalPSD`インスタンスを構築します。

# 引数

  * `ω::AbstractVector{<:Real}`: 角周波数のベクトル。
  * `p::AbstractVector{<:Real}`: `ω`の周波数に対応するパワースペクトル密度値のベクトル。

# 戻り値

手動で事前に指定されたパワースペクトル密度値を持つ離散化された`EmpiricalPSD`インスタンス。

# 例

```julia
w = 0:0.1:10
p_values = rand(length(w))  # 例の経験的PSD値
emp_psd = EmpiricalPSD(w, p_values)
```
