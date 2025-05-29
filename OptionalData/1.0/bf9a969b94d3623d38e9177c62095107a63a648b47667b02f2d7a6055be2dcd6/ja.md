# OptionalData

このパッケージは、`@OptionalData`マクロと、nullable値（型`Union{T, Nothing} where T`）の薄いラッパーである`OptData`型を提供します。これにより、ランタイムでグローバルに利用可能なデータを型安全にロードおよびアクセスすることができます。

## 使用法

*OptionalData*には以下の使用ケースがあります：

1. パッケージの一部がインターネットからのデータに依存している一方で、他の部分は依存していない場合。ネットワーク障害が発生した場合、パッケージは劣化した体験を提供する必要がありますが、独立した部分は引き続き機能するべきです。
2. パッケージが手動の初期化ステップを必要とする場合、例えばユーザーが提供したファイルからデータをロードする場合、データの可用性をチェックするコードを繰り返し書きたくない場合です。

`@OptionalData`マクロを使用してオプショナルなグローバルデータを宣言します：

```julia
using OptionalData

# @OptionalData name type [error_msg]
@OptionalData OPT_FLOAT Float64 "忘れてロードしていませんか？"

# これは次のように展開されます
const OPT_FLOAT = OptData{Float64}(string(:OPT_FLOAT), "忘れてロードしていませんか？")
```

`get`を使用してその値にアクセスし、`isavailable`で利用可能かどうかを確認します：

```julia
# これは`NoDataError`をスローします。なぜならOPT_FLOATはまだ値を含んでいないからです。
get(OPT_FLOAT)
# ERROR: OPT_FLOATは利用できません。忘れてロードしていませんか？
isavailable(OPT_FLOAT) == false
```

`push!`を使用してデータをロードします：

```julia
push!(OPT_FLOAT, 3.0)
isavailable(OPT_FLOAT) == true
get(OPT_FLOAT) == 3.0
```
