```
fmi2Reset(c::FMU2Component; soft::Bool=false)
```

シミュレーション実行後にFMUをリセットするために環境によって呼び出されます。FMUは、fmi2Instantiateが呼び出されたかのように同じ状態になります。すべての変数はデフォルト値を持ちます。新しい実行を開始する前に、fmi2SetupExperimentとfmi2EnterInitializationModeを呼び出す必要があります。

# 引数

  * `c::FMU2Component`: 引数 `c` は、FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体です。

# キーワード

  * `soft::Bool=false`: キーワード `soft = true` の場合、このコマンドはFMUがこのコマンドに対して許可された状態にある場合にのみ実行されます。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.3 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.3[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.3[p.18]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.3[p.22]: 2.1.6 FMUの初期化、終了、およびリセット

また、[`fmi2Terminate`](@ref)も参照してください。
