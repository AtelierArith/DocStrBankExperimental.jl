```
fmiCompletedIntegratorStep(c::FMU2Component, noSetFMUStatePriorToCurrentPoint::fmi2Boolean)
```

この関数は、完了したステップの後に環境によって呼び出されなければなりません。

# 引数

  * `C::FMU2Component`: FMI 2.0.2 標準でインスタンス化された FMU のインスタンスを表す可変構造体。
  * `noSetFMUStatePriorToCurrentPoint::fmi2Boolean`: 引数 `noSetFMUStatePriorToCurrentPoint = fmi2True` は、`fmi2SetFMUState` がこのシミュレーション実行中の現在の時間より前の時間瞬間に対してはもはや呼び出されないことを示します。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: 物事は完全に正しくはないが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返される
  * `enterEventMode::Array{fmi2Boolean, 1}`: FMU が `fmi2EnterEventMode` を呼び出すべきかどうかを環境に信号するために `enterEventMode[1]` を返します
  * `terminateSimulation::Array{fmi2Boolean, 1}`: シミュレーションを終了すべきかどうかを信号するために `terminateSimulation[1]` を返します。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

また、[`fmi2CompletedIntegratorStep`](@ref) も参照してください。
