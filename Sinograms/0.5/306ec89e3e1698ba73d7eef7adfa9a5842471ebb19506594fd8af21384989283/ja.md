```
Window{S,T}
```

FBPアポダイジングウィンドウのデータ型で、与えられたウィンドウ `shape::S` と `cutoff::T` を持ちます。

```jldoctest
julia> Window(Hamming(), 0.8)
Window{Hamming, Float64}(Hamming(), 0.8)
```
