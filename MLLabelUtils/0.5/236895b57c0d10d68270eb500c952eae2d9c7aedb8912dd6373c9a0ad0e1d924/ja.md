```
classify(x, encoding)
```

`x`を`encoding`に基づいて分類されたバージョンを返します。つまり、`x`が正のラベルとして解釈できる場合、`encoding`の正のラベルが返されます。そうでない場合は負のラベルが返されます。

```
julia> classify(0.6, LabelEnc.ZeroOne(UInt8))
0x01

julia> classify(0.4, LabelEnc.ZeroOne(UInt8))
0x00

julia> classify([0.1,0.2,0.6,0.1], LabelEnc.OneOfK)
3
```
