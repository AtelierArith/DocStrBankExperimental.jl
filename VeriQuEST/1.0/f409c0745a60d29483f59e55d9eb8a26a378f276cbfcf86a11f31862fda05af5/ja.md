```
compute_angle_δᵥ(::ComputationRound,::NoInputQubits,ϕ,Sx,Sz,θᵥ,rᵥ)
```

与えられたパラメータに基づいて角度 δᵥ を計算します。

δᵥ の計算ケース

4. ラウンド ≡ 計算 ∩ キュービット ∉ 入力セット  → δᵥ = ϕᵥ′ + θᵥ + rᵥπ

# 引数

  * `::ComputationRound`: 計算ラウンド。
  * `::NoInputQubits`: 入力キュービットの数。
  * `ϕ`: ϕ の値。
  * `Sx`: Sx の値。
  * `Sz`: Sz の値。
  * `θᵥ`: θᵥ の値。
  * `rᵥ`: rᵥ の値。

# 戻り値

  * `δᵥ`: 計算された角度 δᵥ。

# 例

```julia
julia> compute_angle_δᵥ(ComputationRound(),NoInputQubits(),0,0,[0,0,0],0,0)
0
```
