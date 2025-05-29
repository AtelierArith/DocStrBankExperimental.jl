```
fmi2CancelStep(c::FMU2Component)
```

`fmi2DoStep`が`fmi2Pending`を返した場合に、現在の非同期実行を停止するために呼び出すことができます。

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準におけるインスタンス化されたFMUのインスタンスを表す可変構造体。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: 問題なし
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.104]: 4.2.2 計算

また[`fmi2DoStep`](@ref)も参照してください。
