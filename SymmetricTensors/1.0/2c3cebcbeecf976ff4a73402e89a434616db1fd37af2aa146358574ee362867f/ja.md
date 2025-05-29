```
rand(::Type{SymmetricTensor{T, N}}, n::Int, b::Int = 2)
```

$$
N
$$

次元のランダムな`SymmetricTensor`を返します。要素の型は`T`で、$[0, 1)$の一様分布から抽出されます。ここで、`n`はデータサイズを、`b`はブロックサイズを示します。
