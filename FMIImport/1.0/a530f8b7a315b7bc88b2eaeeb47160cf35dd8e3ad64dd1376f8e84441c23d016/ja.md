```
fmi3EnterInitializationMode(c::FMU3Instance, startTime::Union{Real, Nothing} = nothing, stopTime::Union{Real, Nothing} = nothing; tolerance::Union{Real, Nothing} = nothing)
```

FMUは初期化モードに入ります。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `startTime::Union{Real, Nothing} = nothing`: `startTime`は実数で、実験の開始時間の値を設定します。何もしない場合はデフォルト値が自動的に設定されます（デフォルト = `nothing`）。
  * `stopTime::Union{Real, Nothing} = nothing`: `stopTime`は実数で、実験の終了時間の値を設定します。何もしない場合はデフォルト値が自動的に設定されます（デフォルト = `nothing`）。

# キーワード

  * `tolerance::Union{Real, Nothing} = nothing`: `tolerance`は実数で、許容範囲の値を設定します。何もしない場合はデフォルト値が自動的に設定されます（デフォルト = `nothing`）。

# 戻り値

  * `str.state`が`fmi3InstanceStateInstantiated`で呼び出されていない場合は警告を返します。
  * `status::fmi3Status`: 戻り値`status`は`fmi3Status`型の列挙で、関数呼び出しの成功を示します。

詳細:

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.2. 状態: インスタンス化された

[`fmi3EnterInitializationMode`](@ref)も参照してください。
