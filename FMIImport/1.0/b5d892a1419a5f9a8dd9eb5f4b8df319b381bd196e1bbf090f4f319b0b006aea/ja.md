```
fmi2DeSerializeFMUstate!(c::FMU2Component, serializedState::AbstractArray{fmi2Byte}, size::Csize_t, FMUstate::Ref{fmi2FMUstate})
```

バイトベクター `serializedState` を長さ `size` でデシリアライズし、FMU状態のコピーを構築し、参照 `FMUstate` の指定されたアドレスにFMU状態を格納します。このポインタはこのコピーを指します。

# 引数

  * `str::FMU2Component`: ミュータブル構造体で、FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `state::fmi2FMUstate`: 引数 `state` は、実際または以前の時間瞬間の内部FMU状態を保存するFMU内のデータ構造へのポインタです。
  * `serialzedState::AbstractArray{fmi2Byte}`: 引数 `serializedState` は、ポインタ `FMUstate` によって参照されるシリアライズされたデータのコピーを含みます。
  * `size::Csize_t`: 引数 `size` は、シリアライズされたベクターの長さを定義します。
  * `FMUstate::Ref{fmi2FMUstate}`: 引数 `FMUstate` は、実際または以前の時間瞬間の内部FMU状態を保存するFMU内のデータ構造へのポインタである `fmi3FMUstate` 型のデータを安全に参照するオブジェクトです。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: 物事は完全に正しくはないが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

# ソース

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.25]: 2.1.8 完全なFMU状態の取得と設定

また、[`fmi2DeSerializeFMUstate!`](@ref)も参照してください。
