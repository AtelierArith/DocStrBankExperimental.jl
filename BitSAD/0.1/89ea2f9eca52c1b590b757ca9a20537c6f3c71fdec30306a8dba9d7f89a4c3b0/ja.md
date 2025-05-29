```
generate(s::SBitstream, T::Integer = 1)
generate!(s::SBitstream, T::Integer = 1)
```

ビットストリーム `s` の `T` サンプルを生成します。これらを `generate!` のキューに追加し、そうでなければビットのベクターを返します。
