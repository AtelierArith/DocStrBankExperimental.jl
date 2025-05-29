fmi3SerializeFMUState(c::FMU3Instance, state::fmi3FMUState)

ポインタ FMUstate が参照するデータをシリアライズし、このデータを環境によって提供される長さ size のバイトベクター serializedState にコピーします。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表します。
  * `serializedState::Array{fmi3Byte}`: 引数 `serializedState` はデシリアライズされる fmi3Byte フィールドを含みます。

# 戻り値

  * 戻り値 `state` は内部 FMU 状態のコピーへのポインタです。

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存定義
  * FMISpec3.0: 2.2.6.4. 完全な FMU 状態の取得と設定

また、[`fmi3DeSerializeFMUState`](@ref) も参照してください。
