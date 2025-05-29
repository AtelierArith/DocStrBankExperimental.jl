```
constraints_opex_fixed(m, n::Node, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
constraints_opex_fixed(m, n::Storage, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
constraints_opex_fixed(m, n::Sink, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
```

汎用の[`Node`](@ref)、[`Storage`](@ref)、および[`Sink`](@ref)の固定OPEXに関する制約を作成するための関数です。

この関数は、`Node`に対して他の方法が指定されていない場合のフォールバックオプションとして機能します。

`Storage`ノードのフォールバックオプションには、ノードが対応するストレージパラメータを持っている場合の`charge`、`level`、および`discharge`の固定OPEXが含まれます。個々の寄与は、すべての状況で設置された容量に基づいて計算されます。

`Storage`ノードの場合、フォールバックオプションには、ノードが対応するストレージパラメータを持っている場合の`charge`、`level`、および`discharge`の固定OPEXが含まれます。個々の寄与は、すべての状況で設置された容量に基づいて計算されます。

`Sink`ノードの場合、フォールバックオプションは変数`:opex_fixed`の値を0に固定します。
