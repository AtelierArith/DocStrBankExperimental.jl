```
fmi3CompletedIntegratorStep!(c::FMU3Instance,
                                  noSetFMUStatePriorToCurrentPoint::fmi3Boolean,
                                  enterEventMode::Ref{fmi3Boolean},
                                  terminateSimulation::Ref{fmi3Boolean})
```

この関数は、環境によって、統合器の完了したステップの後に呼び出されなければなりません。能力フラグ `needsCompletedIntegratorStep == true` が設定されている場合です。`enterEventMode == fmi3True` の場合、イベントモードに入る必要があります。`terminateSimulation == fmi3True` の場合、シミュレーションは終了されるべきです。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0標準のFMUのインスタンス化されたインスタンスを表します。
  * `noSetFMUStatePriorToCurrentPoint::fmi3Boolean`: 引数 `noSetFMUStatePriorToCurrentPoint = fmi3True` は、`fmi3SetFMUState` がこのシミュレーション実行中の現在の時間より前の時間瞬間に対してはもはや呼び出されないことを示します。
  * `enterEventMode::Ref{fmi3Boolean}`: 引数 `enterEventMode` は、FMUが `fmi3EnterEventMode` を呼び出すべきかどうかを環境に信号する戻り値（fmi3Boolean）を指します。`fmi3Boolean` は `Boolean` データ型のエイリアスタイプです。
  * `terminateSimulation::Ref{fmi3Boolean}`: 引数 `terminateSimulation` は、シミュレーションを終了すべきかどうかを信号する戻り値（fmi3Boolean）を指します。`fmi3Boolean` は `Boolean` データ型のエイリアスタイプです。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: 物事は完全に正しくはないが、計算は続行可能
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 3.2.1. 状態: 連続時間モード

また [`fmi3CompletedIntegratorStep!`](@ref) も参照してください。
