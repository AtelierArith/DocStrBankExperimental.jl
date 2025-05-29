```
expectation_value(pf::InfinitePartitionFunction, inds => O, env::CTMRGEnv)
```

局所テンソル `O` を分配関数 `pf` の位置 `inds` に挿入し、与えられた CTMRG 環境 `env` を使用してコントラクトを行うことに対応する期待値を計算します。

ここで `inds` は `Tuple{Int,Int}` または `CartesianIndex{2}` として指定でき、`O` は [`PartitionFunctionTensor`](@ref) インデックス規約に従うランク4テンソルである必要があります。
