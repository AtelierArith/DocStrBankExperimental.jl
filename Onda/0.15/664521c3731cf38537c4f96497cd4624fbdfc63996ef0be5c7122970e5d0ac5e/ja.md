```
load(signal[, span_relative_to_loaded_samples]; encoded::Bool=false)
load(file_path, file_format::Union{AbstractString,AbstractLPCMFormat},
     info[, span_relative_to_loaded_samples]; encoded::Bool=false)
```

`signal`/`file_path`/`file_format`/`info`で説明される`Samples`オブジェクトを返します。

`span_relative_to_loaded_samples`が存在する場合、`load(...)[:, span_relative_to_loaded_samples]`を返しますが、返されない中間サンプルデータの読み込みを避けるように試みます。この最適化された方法の効果は、`file_path`の型（すなわち、`Onda.read_byte_range(::typeof(file_path), ...)`に対して高速なメソッドが定義されているかどうか）および`file_format`の型（すなわち、対応するフォーマットがランダムまたはチャンクアクセスをサポートしているかどうか）に依存します。

`encoded`が`true`の場合、返す前に`Samples`オブジェクトをデコードしないでください。
