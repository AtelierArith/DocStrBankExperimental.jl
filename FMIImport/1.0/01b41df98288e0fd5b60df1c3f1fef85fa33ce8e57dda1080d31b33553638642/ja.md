```
fmi2SetupExperiment(c::FMU2Component, toleranceDefined::fmi2Boolean, tolerance::fmi2Real, startTime::fmi2Real, stopTimeDefined::fmi2Boolean, stopTime::fmi2Real)
```

FMUに実験を設定するように指示します。この関数は、`fmi2Instantiate`の後に呼び出され、`fmi2EnterInitializationMode`が呼び出される前に呼び出す必要があります。

# 引数

  * `c::FMU2Component`: 引数`c`は、FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体です。
  * `toleranceDefined::fmi2Boolean`: 引数`toleranceDefined`はFMUのタイプに依存します：

      * fmuType = fmi2ModelExchange: `toleranceDefined = fmi2True`の場合、モデルは数値積分スキームで呼び出され、ステップサイズは誤差推定のために`tolerance`を使用して制御されます。この場合、モデル内で使用されるすべての数値アルゴリズム（例えば、非線形代数方程式を解くためのもの）は、適切な小さい相対誤差の推定で動作する必要があります。
      * fmuType = fmi2CoSimulation: `toleranceDefined = fmi2True`の場合、スレーブの通信間隔は誤差推定によって制御されます。スレーブが可変ステップサイズと誤差推定を持つ数値積分器を利用する場合、内部積分器の誤差推定に「tolerance」を使用することが推奨されます（通常は相対誤差として）。コシミュレーション用のFMUはこの引数を無視する可能性があります。
  * `startTime::fmi2Real`: 引数`startTime`は、モデルが与えられた境界内で有効かどうかを確認するため、または結果を保存するために必要なメモリを割り当てるために使用できます。これは独立変数の固定初期値であり、独立変数が`time`の場合、`startTime`は初期化の開始時間です。
  * `stopTimeDefined::fmi2Boolean`: `stopTimeDefined = fmi2True`の場合、stopTimeは独立変数の定義された最終値であり、`stopTimeDefined = fmi2False`の場合、独立変数の最終値は定義されておらず、引数`stopTime`は意味を持ちません。
  * `stopTime::fmi2Real`: 引数`stopTime`は、モデルが与えられた境界内で有効かどうかを確認するため、または結果を保存するために必要なメモリを割り当てるために使用できます。これは独立変数の固定最終値であり、独立変数が「time」の場合、stopTimeはシミュレーションの停止時間です。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙であり、関数呼び出しの成功を示します。

詳細：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行している場合にこのステータスが返されます

# ソース

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.22]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.22]: 2.1.6 FMUの初期化、終了、およびリセット

[`fmi2SetupExperiment`](@ref)も参照してください。
