```
Permutation{p} <: AbstractPermutation
```

コンパイル時の次元置換を説明します。

型パラメータ `p` は、`(3, 1, 2)` のような有効な置換である必要があります。

---

```
Permutation(perm::Vararg{Int})
Permutation(perm::NTuple{N,Int})
```

`Permutation` を構築します。

# 例

両者は同等です：

```julia
p1 = Permutation(3, 4)
p2 = Permutation((3, 4))
```
