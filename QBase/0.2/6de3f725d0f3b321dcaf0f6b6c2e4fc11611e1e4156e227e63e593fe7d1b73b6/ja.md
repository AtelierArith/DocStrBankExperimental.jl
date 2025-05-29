```
bloch_qubit_ket( θ :: Real, ϕ :: Real ) :: Ket{Complex{Float64}}
```

指定された球面座標 `(r=1, θ, ϕ)` に対するキュービットケットを返します：

$$
|\psi\rangle = \cos(\theta/2)|0\rangle + e^{i\phi}\sin(\theta/2)|1\rangle
$$

ケットに位相がない場合は、実数値の `Ket` が構築されます：

```julia
bloch_qubit_ket( θ :: Real ) :: Ket{Float64}
```

入力：

  * `θ ∈ [0, 2π]`: 極角（z軸に対して）
  * `ϕ ∈ [0, 2π]`: 方位角（x-y平面）

入力 `θ` および/または `ϕ` が有効な範囲内でない場合、`DomainError` がスローされます。
