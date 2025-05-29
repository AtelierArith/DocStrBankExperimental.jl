```
fmi2SerializeFMUstate(c::FMU2Component, state::fmi2FMUstate)
```

ポインタ FMUstate が参照するデータをシリアライズし、このデータを環境によって提供されるサイズのバイトベクター serializedState にコピーします。

# 引数

  * `str::fmi2Struct`: FMI 2.0.2 標準における FMU の代表。

より詳細には: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `str::FMU2`: FMI 2.0.2 標準における FMU とそのすべてのインスタンスを表す可変構造体。
  * `str::FMU2Component`: FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表す可変構造体。
  * `state::fmi2FMUstate`: 引数 `state` は、実際のまたは以前の時間瞬間の内部 FMU 状態を保存する FMU 内のデータ構造へのポインタです。

# 戻り値

  * `serializedState:: Array{fmi2Byte}`: 戻り値 `serializedState` には、ポインタ FMUstate が参照するシリアライズされたデータのコピーが含まれます。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.25]: 2.1.8 完全な FMU 状態の取得と設定

また [`fmi2SerializeFMUstate`](@ref) を参照してください。
