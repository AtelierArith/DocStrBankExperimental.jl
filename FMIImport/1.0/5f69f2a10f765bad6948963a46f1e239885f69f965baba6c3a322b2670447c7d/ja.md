```
fmi2SetTime(c::FMU2Component, 
                time::fmi2Real; 
                soft::Bool=false,
                track::Bool=true,
                force::Bool=c.fmu.executionConfig.force,
                time_shift::Bool=c.fmu.executionConfig.autoTimeShift)
```

新しい時間瞬間を設定し、提供された新しい時間値が以前に設定された時間値と異なる場合に、時間に依存する変数のキャッシュを再初期化します（定数またはパラメータのみに依存する変数は、後で新たに計算する必要はなく、以前に計算された値を再利用できます）。

# 引数

  * `c::FMU2Component`: ミュータブル構造体で、FMI 2.0.2標準のFMUのインスタンスを表します。
  * `time::fmi2Real`: 引数 `time` は `fmi2Real` 型の値を含み、これは `Real` データ型のエイリアスタイプです。 `time` は独立変数時間 t を設定します。

# キーワード

  * `soft::Bool=false`: キーワード `soft = true` の場合、このコマンドはFMUがこのコマンドに対して許可された状態にある場合にのみ実行されます。
  * `track::Bool=true`: キーワード `track = true`
  * `time_shift::Bool=c.fmu.executionConfig.autoTimeShift`:

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: 物事は完全に正しくはないが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.1 独立変数の提供とキャッシュの再初期化

[`fmi2SetTime`](@ref) も参照してください。
