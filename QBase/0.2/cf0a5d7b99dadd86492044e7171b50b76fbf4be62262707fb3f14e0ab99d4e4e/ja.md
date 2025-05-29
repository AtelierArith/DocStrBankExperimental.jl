量子状態をブロッホ球上の座標で表現するためのキュービット密度行列を返します。詳細は [`bloch_qubit_ket`](@ref) を参照してください。

球面座標:

ブロッホ球の表面上の状態は、球面座標で表現できます。

```julia
bloch_qubit_state(θ::Real, ϕ::Real) :: State{Complex{Float64}}
```

  * `θ ∈ [0, π]`: 極角（z軸に対して）。
  * `ϕ ∈ [0, 2π]`: 方位角（x-y平面）

直交座標:

ブロッホ球の体積内の状態は、直交座標で表現できます。

```julia
bloch_qubit_state(x::Real, y::Real, z::Real) :: State{Complex{Float64}}
```

  * ここで `x`、`y`、および `z` は単位球に制約され、`0 <= norm([x,y,z]) <= 1` です。

座標 `(x,y,z)` が制約に従わない場合、`DomainError` がスローされます。
