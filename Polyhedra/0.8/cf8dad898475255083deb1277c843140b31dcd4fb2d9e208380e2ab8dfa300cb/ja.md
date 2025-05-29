```
detecthlinearity(hr::HRepresentation, solver; kws...)
```

線形性が検出された新しいH表現を`solver`を使用して返します。

残りのキーワード引数`kws`は[`detect_new_linearities`](@ref)に渡されます。
