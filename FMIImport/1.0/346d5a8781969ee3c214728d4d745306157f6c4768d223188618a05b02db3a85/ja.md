```
fmi3UpdateDiscreteStates(c::FMU3Instance, discreteStatesNeedUpdate::Ref{fmi3Boolean}, terminateSimulation::Ref{fmi3Boolean}, 
                                nominalsOfContinuousStatesChanged::Ref{fmi3Boolean}, valuesOfContinuousStatesChanged::Ref{fmi3Boolean},
                                nextEventTimeDefined::Ref{fmi3Boolean}, nextEventTime::Ref{fmi3Float64})
```

この関数は、現在の超密な時間瞬間で収束した解を示すために呼び出されます。fmi3UpdateDiscreteStatesは、超密な時間瞬間ごとに少なくとも1回呼び出す必要があります。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0標準のFMUのインスタンス化されたインスタンスを表します。
  * `discreteStatesNeedUpdate::Ref{fmi3Boolean}`:
  * `terminateSimulation::Ref{fmi3Boolean}`:
  * `nominalsOfContinuousStatesChanged::Ref{fmi3Boolean}`:
  * `valuesOfContinuousStatesChanged::Ref{fmi3Boolean}`:
  * `nextEventTimeDefined::Ref{fmi3Boolean}`:
  * `nextEventTime::Ref{fmi3Float64}`:

# 戻り値

  * `status::fmi3Status`: 戻り値`status`は`fmi3Status`型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.5. 状態: イベントモード
