```
AllToAllConnectivity <:AbstractConnectivity
```

Anyon Systems QPUの全てのキュービット接続性を記述するデータ構造です。この接続タイプは、[`VirtualQPU`](@ref)のようなシミュレーションされた`QPUs`で遭遇します。

# 例

```jldoctest
julia> connectivity = AllToAllConnectivity()
AllToAllConnectivity()

```
