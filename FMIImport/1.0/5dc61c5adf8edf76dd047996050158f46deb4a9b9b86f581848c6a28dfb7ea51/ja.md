```
fmi2DeSerializeFMUstate(c::FMU2Component, serializedState::AbstractArray{fmi2Byte})
```

serializedState fmi2Byte フィールドのデータをデシリアライズします。

# 引数

  * `c::FMU2Component`: FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表す可変構造体。
  * `serializedState::Array{fmi2Byte}`: 引数 `serializedState` にはデシリアライズされる fmi2Byte フィールドが含まれています。

# 戻り値

  * 戻り値 `state` は内部 FMU 状態のコピーへのポインタです。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.25]: 2.1.8 完全な FMU 状態の取得と設定

他にも [`fmi2DeSerializeFMUstate`](@ref) を参照してください。
