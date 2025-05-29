```
value(g::Group)::Union{BigInt, Tuple{BigInt, BigInt}, Tuple{BitVector, BitVector}}
```

グループインスタンスを最も単純な表現に変換します。一般的にはデバッグ目的で使用され、シリアル化には`octet`を使用するべきです。`octet`は一貫したパディングも保証します。

関連情報として`octet`、`Curves.gx`、`Curves.gy`を参照してください。
