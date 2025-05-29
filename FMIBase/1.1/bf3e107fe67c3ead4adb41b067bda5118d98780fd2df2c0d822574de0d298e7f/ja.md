```
getValue(comp::FMU2Component, vrs::fmi2ValueReferenceFormat)
```

fmi2ValueReferenceを持つmodelVariablesを含むfmi2ScalarVariableの特定の値を配列で返します。

# 引数

  * `comp::FMU2Component`: FMI 2.0.2標準でインスタンス化されたFMUのインスタンスを表す可変構造体。
  * `vrs::fmi2ValueReferenceFormat`: ユーザーがfmi[X]ValueReferenceを渡す方法のワイルドカード

詳細: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# 戻り値

  * `dstArray::Array{Any,1}(undef, length(vrs))`: 入力変数vr（vr = vrs[i]）と同じfmi2ValueReferenceを持つmodelVariablesを含むfmi2ScalarVariableの特定の値を格納します。`dstArray`は`vrs`と同じ長さの1次元配列です。
