```
SMSSpamCollection(; dir=nothing)
```

SMSスパムコレクション v.1（以下、コーパス）は、SMSスパム研究のために収集されたSMSタグ付きメッセージのセットです。これは、5,574件の英語のSMSメッセージのセットを含み、ハム（正当）またはスパムとしてタグ付けされています。コーパスには、合計4,827件のSMS正当メッセージ（86.6%）と、合計747件（13.4%）のスパムメッセージがあります。

コーパスは、Tiago Agostinho de Almeida（http://www.dt.fee.unicamp.br/~tiago）とJosé María Gómez Hidalgo（http://www.esp.uem.es/jmgomez）によって収集されました。

```julia-repl julia> using MLDatasets: SMSSpamCollection

julia> targets = SMSSpamCollection.targets();

julia> summary(targets) "5574-element Vector{Any}"

julia> targets[1] "ham"

julia> summary(features) "5574-element Vector{Any}"
```
