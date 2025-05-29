```
EigSorter(by; rev = false)
```

[`eigsolve`](@ref) または [`schursolve`](@ref) と組み合わせて使用するためのシンプルな `struct` で、`by` でソートされたときに最初に現れる固有値、そして `rev == true` の場合は逆順で現れる固有値をターゲットにすることを示します。
