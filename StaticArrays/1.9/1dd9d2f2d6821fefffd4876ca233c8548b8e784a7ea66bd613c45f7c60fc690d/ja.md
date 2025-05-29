```
@SMatrix [a b c d]
@SMatrix [[a, b];[c, d]]
@SMatrix [i+j for i in 1:2, j in 1:2]
@SMatrix ones(2, 2)
```

`SMatrix`を構築するための便利なマクロです。詳細な機能については[`@SArray`](@ref)を参照してください。
