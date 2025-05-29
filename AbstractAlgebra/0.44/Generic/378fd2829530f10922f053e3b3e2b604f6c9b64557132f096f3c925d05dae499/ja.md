```
dim(Y::YoungTableau) -> BigInt
```

パーティション `Y.part` に関連する置換群 $S_n$ の不可約表現の次元（フック長公式を使用）を返します。

計算が容易にオーバーフローするため、`BigInt` が返されます。異なる型で次元の計算を行うには、`dim(Int, Y)` を呼び出すことができます。

# 例

```jldoctest
julia> dim(YoungTableau([4,3,1]))
70

julia> dim(YoungTableau([3,1])) # S_4 の通常表現
3
```
