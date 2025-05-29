```
function client_data(app::T)::String where {T<:ReactiveModel}
```

ブラウザでのみ表示される追加データを定義します。

これは、一時的なデータ、例えば最初に検証を通過する必要があるフォームデータを保持するためのものです。このデータを使用するには、おそらく [`js_methods`](@ref) も定義したいでしょう。

### 例

```julia
import Stipple.client_data
client_data(m::Example) = client_data(client_name = js"null", client_age = js"null", accept = false)
```

これは、モデル `Example` のために追加のフィールド `client_name`、`client_age`、および `accept` を定義します。これらはもちろん、モデルの既存のフィールドと重複しないようにするべきです。
