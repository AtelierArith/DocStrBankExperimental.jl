```
Prometheus.Family{C}(name, help, args..., label_names; registry=DEFAULT_REGISTRY, kwargs...)
```

ラベル `label_names` によって与えられたラベルを持つコレクタファミリーを作成します。新しいラベル値のセットが見つかるたびに、タイプ `C <: Collector` の新しいコレクタが作成されます。詳細は [`Prometheus.labels`](@ref) を参照してください。

**引数**

  * `name :: String`: ファミリーメトリックの名前。
  * `help :: String`: ファミリーメトリックのドキュメント。
  * `args...`: `C` のコンストラクタに必要な追加の位置引数。詳細は [`Prometheus.labels`](@ref) を参照してください。
  * `label_names`: ファミリーのラベル名。ラベル名は以下のいずれかの形式で指定できます（通常、後で与えられるメソッドのラベル値に一致します。詳細は [`Prometheus.labels`](@ref) を参照してください）：

      * シンボルまたは文字列のタプル、例: `(:target, :status_code)` または `("target", "status_code")`
      * 名前付きタプル型、例: `@NamedTuple{target::String, status_code::Int}` で、名前がラベル名として使用されます。
      * カスタム構造体型、例: `RequestLabels` は以下のように定義されます。

        ```julia
        struct RequestLabels
            target::String
            status_code::Int
        end
        ```

        フィールド名がラベル名として使用されます。

**キーワード引数**

  * `registry :: Prometheus.CollectorRegistry`: コレクタを登録するレジストリ。指定しない場合はデフォルトのレジストリが使用されます。登録をスキップするには `registry = nothing` を渡します。
  * `kwargs...`: `C` のコンストラクタに必要な追加のキーワード引数。詳細は [`Prometheus.labels`](@ref) を参照してください。

**メソッド**

  * [`Prometheus.labels`](@ref): 特定のラベルセットのコレクタを取得または作成します。
  * [`Prometheus.remove`](@ref): 特定のラベルセットのコレクタを削除します。
  * [`Prometheus.clear`](@ref): ファミリー内のすべてのコレクタを削除します。

# 例

```julia
# カウンタのファミリーを構築
counter_family = Prometheus.Family{Counter}(
    "http_requests", "HTTPリクエストの数", (:target, :status_code),
)

# ラベル `target="/api"` と `status_code=200` のカウンタをインクリメント
Prometheus.inc(Prometheus.labels(counter_family, (target="/api", status_code=200)))
```
