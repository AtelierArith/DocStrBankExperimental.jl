```
wsum!(R::AbstractArray, A::AbstractArray,
      w::AbstractVector, dim::Int;
      init::Bool=true)
```

`A`の重み付き合計を重み`w`で次元`dim`にわたって計算し、結果を`R`に格納します。`init=false`の場合、合計はゼロから始まるのではなく、`R`に加算されます。
