```
fastdensesparsemul!(C, A, B, α, β)
```

BLASのようなインターフェースで、`C .= β*C + α*A*B`を計算しますが、Baseよりもはるかに高速です。

また、`Polyester.jl`を使用したマルチスレッド版の`fastdensesparsemul_threaded!`も参照してください。
