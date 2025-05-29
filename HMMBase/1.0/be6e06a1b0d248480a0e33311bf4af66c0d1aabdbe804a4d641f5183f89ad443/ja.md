```
remapseq(seq, ref) -> Vector{Integer}
```

`ref`との重複を最大化する`seq`インデックスの順列を見つけます。

**引数**

  * `seq::Vector{Integer}`: 再マッピングされるシーケンス。
  * `ref::Vector{Integer}`: 参照シーケンス。

**例**

```julia
ref = [1,1,2,2,3,3]
seq = [2,2,3,3,1,1]
remapseq(seq, ref)
# [1,1,2,2,3,3]
```
