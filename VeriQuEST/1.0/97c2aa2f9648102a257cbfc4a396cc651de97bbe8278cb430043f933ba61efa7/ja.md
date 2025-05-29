```
measure_along_ϕ_basis!(client::Client, ψ, v::Union{Int32,Int64}, ϕ::Float64)
```

この関数は、特定の基底に沿って量子状態を測定します。最初に状態にZ回転を適用し、次にハダマードゲートを適用し、最後に測定を行います。基底は角度ϕによって決まります。

# 引数

  * `client::Client`: クライアントオブジェクト。
  * `ψ`: 測定される量子状態。
  * `v::Union{Int32,Int64}`: 操作が適用される頂点。
  * `ϕ::Float64`: 測定の基底を決定する角度。

# 戻り値

  * 測定の結果。

# 例

```julia
client = Client()
ψ = QuantumState()
v = 1
ϕ = π/4
measure_along_ϕ_basis!(client, ψ, v, ϕ)
```
