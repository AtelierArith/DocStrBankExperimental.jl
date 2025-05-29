```
neglabel(encoding)
```

エンコーディングがバイナリの場合、それの負のラベルを返します。それ以外の場合、関数はエラーをスローします。

```
julia> neglabel(LabelEnc.MarginBased(Float32))
-1.0f0
```
