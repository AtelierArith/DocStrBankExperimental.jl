```
listMaxima(SITE_PATTERN_DATA)
```

# 説明

局所的な極大値または臨界点のリストを、対数尤度でソートして返します。`fourLeafMLE()`関数との唯一の違いは、`listMaxima`がグローバル最適解を達成しない臨界点をフィルタリングしないことです。`fourLeafMLE()`のドキュメントを参照してください。

# 使用例:

```

random_hadamard_edge_parameters=rand(5)
test_model=computeProbabilityVector(random_hadamard_edge_parameters,1)
N=1000
SITE_PATTERN_DATA = rand(Multinomial(N,test_model))
listMaxima(SITE_PATTERN_DATA)

```
