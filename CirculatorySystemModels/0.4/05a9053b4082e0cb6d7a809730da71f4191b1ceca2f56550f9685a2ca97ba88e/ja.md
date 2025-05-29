`VariableElastance(; name, V₀=0.0, C=1.0, Escale=1.0, fun, inP=false, has_ep=false, has_variable_ep=false, p₀=0.0)`

`VariableElastance`は`Elastance`要素に基づいて定義されていますが、筋繊維の収縮をモデル化する時間変化する弾性関数を持っています。

名前付きパラメータ：

`V₀`:              ストレスフリーの体積（ゼロ圧力体積）

`Escale`:          スケーリングファクター（弾性ファクター）

`fun`:             弾性のための関数オブジェクト（`fun(t)`でなければなりません）

`inP`:             （Bool）dp/dtで定式化する（デフォルト：false）

`has_ep`:          （Bool）trueの場合、圧力オフセットのためのパラメータ`p₀`を追加します                    例：胸腔圧（デフォルト：false）

`p₀`:              mmHgでの外部圧力（例：胸腔圧、デフォルト：0.0）                    *注：この引数が設定されている場合、`has*ep`が`false`であっても使用されます。`has*ep`は`p₀`がパラメータとして公開されるかどうかを制御するだけです！*

`has*variable*ep`: （Bool）可変外部圧力のためのピンを公開する（デフォルト：false）                    このピンは、外部圧力を提供する別のピンまたは関数に接続できます。                    *注：`has*variable*ep`が`true`に設定されている場合、このピンは作成され、`has*ep`に依存しません！*
