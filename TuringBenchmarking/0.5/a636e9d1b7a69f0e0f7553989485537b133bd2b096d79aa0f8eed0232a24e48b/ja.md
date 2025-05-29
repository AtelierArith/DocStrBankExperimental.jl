```
make_turing_suite(model::Turing.Model; kwargs...)
```

`model`のデフォルトベンチマークスイートを作成します。

# キーワード引数

  * `adbackends`: 使用するadbackendsのコレクションで、ADTypes.jlからの型または`Symbol`を使用して指定します。デフォルトは`ADTypes.AbstractADType[ADTypes.AutoForwardDiff(chunksize=0), ADTypes.AutoReverseDiff(), ADTypes.AutoReverseDiff(compile=true), ADTypes.AutoZygote()]`です。
  * `run_once=true`: `true`の場合、各ベンチマークの本体が1回実行され、コンパイルがタイミングに含まれないようにします（コンパイルが許可された時間制限を超える場合に発生する可能性があります）。
  * `check=false`: `true`の場合、対数密度評価と勾配が互いに比較され、一貫性があることが確認されます。これにより`run_once=true`が強制されることに注意してください。
  * `error_on_failed_check=false`: `true`の場合、チェックが失敗した場合に警告を表示するのではなくエラーがスローされます（デフォルトでは警告が表示されます）。
  * `error_on_failed_backend=false`: `true`の場合、バックエンドのいずれかの対数密度または勾配の評価が失敗した場合に警告を表示するのではなくエラーがスローされます（デフォルトでは警告が表示されます）。
  * `varinfo`: 使用する`VarInfo`。デフォルトは`DynamicPPL.VarInfo(model)`です。
  * `sampler`: 使用する`Sampler`。デフォルトは`nothing`（すなわち、サンプラーなし）です。
  * `context`: 使用する`Context`。デフォルトは`DynamicPPL.DefaultContext()`です。
  * `θ`: 使用するパラメータ。デフォルトは`rand(Vector, model)`です。
  * `θ_linked`: 使用するリンクされたパラメータ。デフォルトは`randn(d)`で、`d`はリンクされたパラメータの長さです。
  * `atol`: 比較に使用する絶対許容誤差。
  * `rtol`: 比較に使用する相対許容誤差。

# 注意事項

  * 各テストのために別の「パラメータ」インスタンス（`DynamicPPL.VarInfo`）が作成されます。したがって、特に大きなモデルがある場合は、一度に1つの`adbackend`のみを渡すことをお勧めします。
