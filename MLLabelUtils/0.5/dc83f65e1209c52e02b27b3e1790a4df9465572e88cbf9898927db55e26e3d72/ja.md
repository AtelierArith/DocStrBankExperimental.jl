```
ind2label(index, encoding)
```

与えられた `index` を `encoding` によって定義された対応するラベルに変換します。バイナリの場合、`index == 1` は正のラベルを表し、`index == 2` は負のラベルを表すことに注意してください。

```
julia> ind2label(1, LabelEnc.ZeroOne(Float32))
1.0f0

julia> ind2label(2, LabelEnc.ZeroOne(Float32))
0.0f0
```
