```
drawline(func::Function, ci1::CartesianIndex{2}, ci2::CartesianIndex{2}, eachstep::Bool=false)
```

`ci1` から `ci2` までの線に沿った各ステップで、ピクセルの行、列の座標を `Tuple{Int, Int}` として単一の引数で `func` を呼び出します。

`eachstep=true` の場合、行が変わるときに `func` が1回呼び出され、列が変わるときにも1回呼び出されます。`eachstep=false` の場合、`func` はより少ない頻度で呼び出され、呼び出しの間に行と列の両方が変わることがあります。
