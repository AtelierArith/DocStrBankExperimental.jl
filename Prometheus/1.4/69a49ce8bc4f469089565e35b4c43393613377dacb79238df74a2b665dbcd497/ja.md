```
Prometheus.labels(family::Family{C}, label_values) where C
```

指定された `label_values` に対応するファミリーからタイプ `C` のコレクターを取得または作成します。入力ラベルに対してコレクターが存在しない場合は、`C` コンストラクターを呼び出して新しいコレクターが作成されます。これは `C(name, help, args...; kwargs..., registry=nothing)` の形式で、`name`、`help`、`args...`、および `kwargs...` はファミリーコンストラクターからの引数です。詳細は [`Family`](@ref) を参照してください。

[`Family`](@ref) を作成する際と同様に、`label_values` は次のいずれかの形式で指定できます。

  * タプル、例: `("/api", 200)`
  * ラベル名に一致する名前を持つ名前付きタプル、例: `(target="/api", status_code=200)`
  * ラベル名に一致するフィールド名を持つ構造体インスタンス、例: `RequestLabels("/api", 200)`

すべての非文字列値（例: 上記の例の `200`）は `string` を使用して文字列化されます。

!!! tip
    `Base.getindex` はファミリーコレクターに対して `Prometheus.labels` の意味を持つようにオーバーロードされています: `family[label_values]` は `Prometheus.labels(family, label_values)` と同等です。


!!! note
    このメソッドはロックの取得/解放と辞書の検索を行い、ラベル名に一致するコレクターを見つけます。典型的なアプリケーションではこのオーバーヘッドは問題になりません（基本的なベンチマークでは100ns未満）が、必要に応じて返されたコレクターをキャッシュすることは安全です。

