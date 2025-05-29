```
fmi3InstantiateModelExchange!(fmu::FMU3; instanceName::String=fmu.modelName, type::fmi3Type=fmu.type, pushInstances::Bool = true, visible::Bool = false, loggingOn::Bool = fmu.executionConfig.loggingOn, externalCallbacks::Bool = fmu.executionConfig.externalCallbacks,
    logStatusOK::Bool=true, logStatusWarning::Bool=true, logStatusDiscard::Bool=true, logStatusError::Bool=true, logStatusFatal::Bool=true)
```

指定されたfmuの新しいmodelExchangeインスタンスを作成し、`logginOn == true`の場合はロガーを追加します。

# 引数

  * `fmu::FMU3`: FMI 3.0標準におけるFMUとそのすべてのインスタンスを表す可変構造体。

# キーワード

  * `instanceName::String=fmu.modelName`: インスタンスの名前
  * `type::fmi3Type=fmu.type`: コシミュレーションまたはモデル交換が存在するかどうかを定義します
  * `pushInstances::Bool = true`: fmuインスタンスをアプリケーションにプッシュするかどうかを定義します。
  * `visible::Bool = false`: FMUがグラフィックインターフェースで起動されるべきかどうか（サポートされている場合、デフォルト=`false`）
  * `loggingOn::Bool = fmu.executionConfig.loggingOn`: FMUが関数呼び出しをログおよび表示するべきかどうか（デフォルト=`false`）
  * `externalCallbacks::Bool = fmu.executionConfig.externalCallbacks`: fmi3CallbackFunctionsに外部共有ライブラリを使用するべきかどうか、これによりログメッセージの可読性が向上する可能性があります（デフォルト=`false`）
  * `logStatusOK::Bool=true`: `fmi3OK`の種類のステータスをログするかどうか（デフォルト=`true`）
  * `logStatusWarning::Bool=true`: `fmi3Warning`の種類のステータスをログするかどうか（デフォルト=`true`）
  * `logStatusDiscard::Bool=true`: `fmi3Discard`の種類のステータスをログするかどうか（デフォルト=`true`）
  * `logStatusError::Bool=true`: `fmi3Error`の種類のステータスをログするかどうか（デフォルト=`true`）
  * `logStatusFatal::Bool=true`: `fmi3Fatal`の種類のステータスをログするかどうか（デフォルト=`true`）

# 戻り値

  * 新しいFMU modelExchangeインスタンスのインスタンスを返します。

# ソース

  * FMISpec3.0リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.4.7 モデル変数
  * FMISpec3.0: 2.3.1. スーパー状態: FMU状態設定可能

他にも[`fmi3InstantiateModelExchange`](#@ref)を参照してください。
