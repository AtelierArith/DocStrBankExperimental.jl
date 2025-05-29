```
AwsQuantumTask(device_arn::String, task_spec; kwargs...)
```

`device_arn`に関連付けられたデバイス上で、`task_spec`に基づいて[`AwsQuantumTask`](@ref)を起動します。

`task_spec`は次のいずれかでなければなりません：

  * `OpenQASMProgram`
  * `BlackbirdProgram`
  * `Problem`
  * `Program`
  * [`Circuit`](@ref)
  * `AHSProgram`
  * [`AnalogHamiltonianSimulation`](@ref)

有効な`kwargs`は次のとおりです：

  * `s3_destination_folder::Tuple{String, String}`、デフォルト値は`default_task_bucket()`です。
  * `shots::Int` - 実行するショットの数、デフォルト値は1000です。値は特定のデバイスの`0`と`MAX_SHOTS`の間でなければなりません。
  * `device_params::Dict{String, Any}` - デバイス固有のパラメータ。現在はDWaveデバイスとシミュレーターにのみ使用されます。
  * `disable_qubit_rewiring::Bool` - コンパイル段階でのキュービットの再配線を許可するかどうか。デフォルトは`false`です。
  * `poll_timeout_seconds::Int` - 結果をポーリングする間に待機する最大秒数。デフォルト：432000
  * `poll_interval_seconds::Int` - 結果をポーリングする間の試行間で待機するデフォルトの秒数。デフォルト：1
  * `tags::Dict{String, String}` - `AwsQuantumTask`のタグ
  * `inputs::Dict{String, Float64}` - `task_spec`内の任意の自由パラメータの入力値

```
