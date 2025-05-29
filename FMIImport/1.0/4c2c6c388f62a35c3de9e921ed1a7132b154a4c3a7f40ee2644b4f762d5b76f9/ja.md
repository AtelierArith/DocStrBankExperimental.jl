```
fmi2Instantiate!(fmu::FMU2;
                    instanceName::String=fmu.modelName,
                    type::fmi2Type=fmu.type,
                    pushComponents::Bool = true,
                    visible::Bool = false,
                    loggingOn::Bool = fmu.executionConfig.loggingOn,
                    externalCallbacks::Bool = fmu.executionConfig.externalCallbacks,
                    logStatusOK::Bool=true,
                    logStatusWarning::Bool=true,
                    logStatusDiscard::Bool=true,
                    logStatusError::Bool=true,
                    logStatusFatal::Bool=true,
                    logStatusPending::Bool=true)
```

指定されたfmuの新しいインスタンスを作成し、logginOn == trueの場合はロガーを追加します。

# 引数

  * `fmu::FMU2`: FMI 2.0.2標準におけるFMUとそのすべてのインスタンスを表す可変構造体。

# キーワード

  * `instanceName::String=fmu.modelName`: インスタンスの名前
  * `type::fmi2Type=fmu.type`: コシミュレーションまたはモデル交換が存在するかどうかを定義します
  * `pushComponents::Bool = true`: fmuコンポーネントをアプリケーションにプッシュするかどうかを定義します。
  * `visible::Bool = false`: FMUがグラフィックインターフェースで起動されるべきかどうか（サポートされている場合、デフォルト=`false`）
  * `loggingOn::Bool = fmu.executionConfig.loggingOn`: FMUが関数呼び出しをログおよび表示するべきかどうか（デフォルト=`false`）
  * `externalCallbacks::Bool = fmu.executionConfig.externalCallbacks`: fmi2CallbackFunctionsに外部共有ライブラリを使用するべきかどうか、これによりログメッセージの可読性が向上する可能性があります（デフォルト=`false`）
  * `logStatusOK::Bool=true`: `fmi2OK`の状態をログするかどうか（デフォルト=`true`）
  * `logStatusWarning::Bool=true`: `fmi2Warning`の状態をログするかどうか（デフォルト=`true`）
  * `logStatusDiscard::Bool=true`: `fmi2Discard`の状態をログするかどうか（デフォルト=`true`）
  * `logStatusError::Bool=true`: `fmi2Error`の状態をログするかどうか（デフォルト=`true`）
  * `logStatusFatal::Bool=true`: `fmi2Fatal`の状態をログするかどうか（デフォルト=`true`）
  * `logStatusPending::Bool=true`: `fmi2Pending`の状態をログするかどうか（デフォルト=`true`）

# 戻り値

  * 新しいFMUコンポーネントのインスタンスを返します。

# ソース

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2: 2.2.7 モデル変数の定義 (ModelVariables)

他の情報は[`fmi2Instantiate`](#@ref)を参照してください。
