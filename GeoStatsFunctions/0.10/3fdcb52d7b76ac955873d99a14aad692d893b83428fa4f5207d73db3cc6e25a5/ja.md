```
MatrixExponentialTransiogram(ball, rate)
```

与えられたメトリック `ball` と遷移 `rate` 行列を持つ行列指数遷移図。

```
MatrixExponentialTransiogram(ball; lengths, proportions)
```

または、名目の `lengths` と相対的な `proportions` から遷移 `rate` 行列を構築します。

```
MatrixExponentialTransiogram(rate; range)
MatrixExponentialTransiogram(rate; ranges, rotation)
```

または、単一の `range` または複数の `ranges` と `rotation` 行列からメトリック `ball` を構築します。

```
MatrixExponentialTransiogram(; range, lengths, proportions)
MatrixExponentialTransiogram(; ranges, rotation, lengths, proportions)
```

または、前のパラメータの組み合わせからメトリック `ball` と遷移 `rate` 行列を構築します。

## 例

```julia
MatrixExponentialTransiogram(lengths=(3.0, 2.0, 1.0), proportions=(1/3, 1/3, 1/3))
MatrixExponentialTransiogram(ranges=(2.0, 1.0))
```

## 参考文献

  * Carle, S.F. & Fogg, G.E. 1996. [Transition probability-based indicator geostatistics](https://link.springer.com/article/10.1007/BF02083656)
  * Carle et al 1998. [Conditional Simulation of Hydrofacies Architecture: A Transition Probability/Markov Approach](https://doi.org/10.2110/sepmcheg.01.147)

### 注意事項

行列指数モデルの最終的な比率は、構築中に指定された相対的な比率とは異なる場合があります。また、平均長さの関数でもあります。
