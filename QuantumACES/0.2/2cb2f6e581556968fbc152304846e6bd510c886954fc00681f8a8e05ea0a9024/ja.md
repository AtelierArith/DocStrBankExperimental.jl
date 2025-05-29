```
AbstractCircuitParameters
```

回路パラメータは、サブタイプ `T <: AbstractCircuitParameters` に格納する必要があります。

次に、これらのパラメータに従って回路を生成する [`get_circuit`](@ref) メソッドを追加します。そのような回路は、[`Circuit`](@ref) オブジェクトであるか、サブタイプ `T <: AbstractCircuit` である必要があります。

# 必要なフィールド

  * `params::Dict{Symbol, Any}`: 回路パラメータの辞書で、特に `layer_time_dict` フィールドを含む必要があります。これは、測定とリセットの時間を含む、回路内の異なるタイプのレイヤーを実装するのにかかる時間の辞書です。
  * `circuit_name::String`: 回路の名前で、パラメータ設定を暗黙的に説明する必要があります。
