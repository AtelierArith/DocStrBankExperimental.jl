```
fmi2SetupExperiment(c::FMU2Component, 
                        startTime::Union{Real, Nothing} = nothing, 
                        stopTime::Union{Real, Nothing} = nothing; 
                        tolerance::Union{Real, Nothing} = nothing)
```

シミュレーションを設定しますが、すべてのパラメータを定義することはありません。

# 引数

  * `c::fmi2Struct`: FMI 2.0.2 標準における FMU の代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: FMI 2.0.2 標準における FMU とそのすべてのインスタンスを表す可変構造体。
  * `c::FMU2Component`: FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表す可変構造体。
  * `startTime::Union{Real, Nothing} = nothing`: `startTime` は実数で、実験の開始時間の値を設定します。何もしない場合はデフォルト値が自動的に設定されます（デフォルト = `nothing`）。
  * `stopTime::Union{Real, Nothing} = nothing`: `stopTime` は実数で、実験の終了時間の値を設定します。何もしない場合はデフォルト値が自動的に設定されます（デフォルト = `nothing`）。

# キーワード

  * `tolerance::Union{Real, Nothing} = nothing`: `tolerance` は実数で、許容範囲の値を設定します。何もしない場合はデフォルト値が自動的に設定されます（デフォルト = `nothing`）。

# 戻り値

  * `str.state` が `fmi2ComponentStateInstantiated` で呼び出されていない場合は警告を返します。
  * `status::fmi2Status`: `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

詳細:

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題がありますが、計算は続行できます
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.23]: 2.1.6 FMU の初期化、終了、およびリセット
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス

[`fmi2SetupExperiment`](@ref) も参照してください。
