```
@MArray [a b; c d]
@MArray [[a, b];[c, d]]
@MArray [i+j for i in 1:2, j in 1:2]
@MArray ones(2, 2, 2)
```

任意の次元の `MArray` を構築するための便利なマクロです。詳細な機能については [`@SArray`](@ref) を参照してください。
