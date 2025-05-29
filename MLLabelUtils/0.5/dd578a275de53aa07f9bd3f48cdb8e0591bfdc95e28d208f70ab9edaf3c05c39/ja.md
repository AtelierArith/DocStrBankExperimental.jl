```
poslabel(encoding)
```

エンコーディングがバイナリの場合、それの正のラベルを返します。それ以外の場合、関数はエラーをスローします。

```
julia> poslabel(LabelEnc.MarginBased(Float32))
1.0f0
```
