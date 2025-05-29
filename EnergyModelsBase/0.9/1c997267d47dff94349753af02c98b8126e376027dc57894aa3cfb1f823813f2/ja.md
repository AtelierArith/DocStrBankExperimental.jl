```
constraints_opex_var(m, n::Node, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
constraints_opex_var(m, n::Storage, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
constraints_opex_var(m, n::Sink, 𝒯ᴵⁿᵛ, modeltype::EnergyModel)
```

汎用の[`Node`](@ref)、[`Storage`](@ref)、および[`Sink`](@ref)の変数OPEXに対する制約を作成するための関数です。

この関数は、`Node`に対して他の方法が指定されていない場合のフォールバックオプションとして機能します。

`Storage`ノードの場合、フォールバックオプションには、ノードが対応するストレージパラメータを持っている場合に、`charge`、`level`、および`discharge`の変数OPEXが含まれます。個々の寄与は、すべての状況で設置された容量に基づいて計算されます。

`Sink`ノードの場合、変数OPEXは、`surplus`と`deficit`の両方のペナルティを通じて計算されます。
