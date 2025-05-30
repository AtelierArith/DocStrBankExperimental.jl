```
lefschetz_subcomplex(lc::LefschetzComplex, subcomp::Vector{Int})
```

Lefschetz複体から部分複体を抽出します。部分複体は局所的に閉じている必要があり、`subcomp`にあるセルのコレクションによって与えられます。
