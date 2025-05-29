```
`HaltonSeq!{T<:AbstractFloat}(H::Vector{T}, B::Int; skip::Int=500)`
```

古いバージョンのHalton.jlからコピーされました。`H`を基数`B`を持つHalton低偏差列のエントリで置き換えます。`H`の要素は区間(0, 1)の値を取ります。キーワード引数`skip`は、ドロップする初期の「バーナイン」要素の数です。
