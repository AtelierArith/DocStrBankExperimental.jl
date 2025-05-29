```
measurement(val::Real, [err::Real]) -> Measurement
measurement(::Missing, [err::Union{Real,Missing}]) -> Missing
val ± err -> Measurement
```

`val`を名目値、`err`を不確実性として`Measurement`オブジェクトを返します。`err`は省略した場合、デフォルトで0になります。

二項演算子`±`は`measurement`と同等であるため、`Measurement`オブジェクトを明示的に`123 ± 4`と書くことで構築できます。

`val`が`missing`の場合、`missing`が返されます。
