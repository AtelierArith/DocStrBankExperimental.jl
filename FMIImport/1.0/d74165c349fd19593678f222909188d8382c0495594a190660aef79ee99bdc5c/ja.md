```
fmi2CompletedIntegratorStep!(c::FMU2Component,
                                noSetFMUStatePriorToCurrentPoint::fmi2Boolean,
                                enterEventMode::Ptr{fmi2Boolean},
                                terminateSimulation::Ptr{fmi2Boolean})
```

この関数は、環境によって、完了した各ステップの後に呼び出されなければなりません。積分器が提供する能力フラグ `completedIntegratorStepNotNeeded = false` の場合です。

# 引数

  * `c::FMU2Component`: 可変構造体で、FMI 2.0.2 標準における FMU のインスタンスを表します。
  * `noSetFMUStatePriorToCurrentPoint::fmi2Boolean`: 引数 `noSetFMUStatePriorToCurrentPoint = fmi2True` は、`fmi2SetFMUState` がこのシミュレーション実行中の現在の時間より前の時間瞬間に対してはもはや呼び出されないことを示します。
  * `enterEventMode::Ref{fmi2Boolean}`: 引数 `enterEventMode` は、FMU が `fmi2EnterEventMode` を呼び出すべきかどうかを環境に通知する戻り値 (fmi2Boolean) を指します。`fmi2Boolean` は `Boolean` データ型のエイリアスタイプです。
  * `terminateSimulation::Ref{fmi2Boolean}`: 引数 `terminateSimulation` は、シミュレーションを終了すべきかどうかを示す戻り値 (fmi2Boolean) を指します。`fmi2Boolean` は `Boolean` データ型のエイリアスタイプです。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: 物事は完全に正しくはないが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

また、[`fmi2CompletedIntegratorStep!`](@ref) も参照してください。
