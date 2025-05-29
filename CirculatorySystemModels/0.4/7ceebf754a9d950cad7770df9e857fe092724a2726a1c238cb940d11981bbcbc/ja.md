`Compliance(; name, V₀=0.0, C=1.0, inP=false, has_ep=false, has_variable_ep=false, p₀=0.0)`

血管のコンプライアンスを実装します。

パラメータは cm, g, s システムで表されます。圧力は mmHg で表されます。`p` は mmHg で計算され、`q` は cm^3/s (ml/s) で計算されます。

名前付きパラメータ:

`V₀`:               ストレスのない体積 ml

`C`:                血管のコンプライアンス ml/mmHg

`inP`:             (Bool) dp/dt で定式化する (デフォルト: false)

`has_ep`:          (Bool) true の場合、圧力オフセットのためのパラメータ `p₀` を追加します                    例: 胸腔圧 (デフォルト: false)

`p₀`:              mmHg での外部圧力 (例: 胸腔圧、デフォルト: 0.0)                    *注意: この引数が設定されている場合、`has*ep`が`false`であっても使用されます。`has*ep`は`p₀`がパラメータとして公開されるかどうかを制御するだけです！*

has*variable*ep`: (Bool) 変動外部圧力のためのピンを公開します (デフォルト: false)                    このピンは、外部圧力を提供する別のピンまたは関数に接続できます。                    _注意:`has*variable*ep`が`true`に設定されている場合、このピンは作成され、`has*ep`に依存しません！_
