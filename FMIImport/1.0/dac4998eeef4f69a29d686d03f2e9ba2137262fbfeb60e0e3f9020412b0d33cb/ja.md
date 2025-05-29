```
fmi3SetDebugLogging(c::FMU3Instance)
```

FMUのDebugLoggerを設定します。

# 引数

  * `c::FMU3Instance`: FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。

# 戻り値

  * `fmi3InstanceStateInstantiated`で`str.state`が呼び出されていない場合は警告を返します。
  * `status::fmi3Status`: 戻り値`status`は`fmi3Status`型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: 問題なし
  * `fmi3Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.1. スーパー状態: FMU状態の設定可能

また[`fmi3SetDebugLogging`](@ref)も参照してください。
