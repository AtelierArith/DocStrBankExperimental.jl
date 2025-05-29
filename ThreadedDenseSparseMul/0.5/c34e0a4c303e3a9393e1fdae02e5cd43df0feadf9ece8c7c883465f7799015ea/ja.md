```
fastdensesparsemul!(C, A, B, α, β)
```

スレッド対応、BLASのようなインターフェースで、`C .= β*C + α*A*B`を計算しますが、Baseよりもはるかに高速です。また、単一スレッド版の`fastdensesparsemul!`も参照してください。
