`asparams`は`TransformVariables.as`に基づいて、特定のパラメータ化された測度のパラメータ空間への双射を構築します。これは連続的なパラメータ空間に対してのみ可能であるため、パラメータの任意の部分集合に値を割り当てるための制約を許可します。

---

```
asparams(::Type{<:ParameterizedMeasure}, ::StaticSymbol)
```

特定のパラメータに対する変換を返します。例えば、

```
julia> asparams(Normal, static(:σ))
asℝ₊
```

---

```
asparams(::Type{<: ParameterizedMeasure{N}}, constraints::NamedTuple) where {N}
```

名前付きタプル`constraints`に従った特定のパラメータ化された測度に対する変換を返します。例えば、

```
julia> asparams(Binomial{(:p,)}, (n=10,))
TransformVariables.TransformTuple{NamedTuple{(:p,), Tuple{TransformVariables.ScaledShiftedLogistic{Float64}}}}((p = as𝕀,), 1)
```

---

```
aspararams(::ParameterizedMeasure)
```

制約のない変換を返します。例えば、

```
julia> asparams(Normal{(:μ,:σ)})
TransformVariables.TransformTuple{NamedTuple{(:μ, :σ), Tuple{TransformVariables.Identity, TransformVariables.ShiftedExp{true, Float64}}}}((μ = asℝ, σ = asℝ₊), 2)
```
