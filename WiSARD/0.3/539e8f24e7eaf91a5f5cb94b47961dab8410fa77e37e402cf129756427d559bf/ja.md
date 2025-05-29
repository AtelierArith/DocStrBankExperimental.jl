```
classify(wnn::WNN, y::Vector{Bool}; bleach=0::Int, gamma=0.5::Float)
```

入力 `y` を分類し、いくつかのラベル `x` を返します。トレーニングが行われていない場合は、代わりに `nothing` が返されます。
