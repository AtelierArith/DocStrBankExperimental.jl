```
fmi3SerializeFMUState(c::FMU3Instance, state::fmi3FMUState)
```

FMUstateによって参照されるデータをシリアライズし、このデータを環境によって提供されるサイズのバイトベクターserializedStateにコピーします。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `state::fmi3FMUState`: 引数`state`は、実際のまたは以前の時間瞬間の内部FMU状態を保存するFMU内のデータ構造へのポインタです。

# 戻り値

  * `serializedState:: Array{fmi3Byte}`: 戻り値`serializedState`は、ポインタFMUstateによって参照されるシリアライズされたデータのコピーを含みます。

# 出典

  * FMISpec3.0リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存定義
  * FMISpec3.0: 2.2.6.4. 完全なFMU状態の取得と設定

他にも[`fmi3SerializeFMUState`](@ref)を参照してください。
