```
HyperLogLog(T = Number)
HyperLogLog{P}(T = Number)
```

データストリームの型 `T` の異なる要素の近似カウントを、`2 ^ P` の「レジスタ」を使用して行います。 `P` は4から16の間の整数でなければなりません（デフォルト）。

デフォルトでは、[1] に定義されている改善されたHyperLogLogカーディナリティ推定器が返されます。

元のHyperLogLog推定器 [2] は、オプション `original_estimator=true` を使用して取得できます。

# 例

```
o = HyperLogLog()
fit!(o, rand(1:100, 10^6))

using Random
o2 = HyperLogLog(String)
fit!(o2, [randstring(20) for i in 1:1000])

# デフォルトでは改善された推定器が返されます：
value(o)
# 元のHyperLogLog推定器は次のように取得できます：
value(o; original_estimator=true)
```

# 参考文献

[1] 改善された推定器: Otmar Ertl. New cardinality estimation algorithms for HyperLogLog sketches. [https://arxiv.org/abs/1702.01284](https://arxiv.org/abs/1702.01284)

[2] 元の推定器: P. Flajolet, Éric Fusy, O. Gandouet, and F. Meunier. Hyperloglog: The analysis of a near-optimal cardinality estimation algorithm. *In Analysis of Algorithms (AOFA)*, pages 127–146, 2007.
