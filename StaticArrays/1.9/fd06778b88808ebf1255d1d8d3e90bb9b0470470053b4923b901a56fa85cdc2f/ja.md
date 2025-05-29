```
@MMatrix [a b c d]
@MMatrix [[a, b];[c, d]]
@MMatrix [i+j for i in 1:2, j in 1:2]
@MMatrix ones(2, 2)
```

`MMatrix`を構築するための便利なマクロです。詳細な機能については[`@SArray`](@ref)を参照してください。
