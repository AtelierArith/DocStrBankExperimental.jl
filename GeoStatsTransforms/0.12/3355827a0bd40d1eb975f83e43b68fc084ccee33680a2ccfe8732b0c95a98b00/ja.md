```
Quenching(transiogram; [options])
```

与えられた理論的 `transiogram` を用いたシミュレーションされたクエンチング (Carle et al. 1998) です。

## オプション

  * `skip`         - シミュレーション中にスキップするインデックス (デフォルトは `[]`)
  * `tol`          - 相対誤差の許容範囲 (デフォルトは `1e-2`)
  * `maxiter`      - 最大反復回数 (デフォルトは `10`)
  * `maxneighbors` - 最大隣接数 (デフォルトは `26`)
  * `rng`          - 擬似乱数生成器 (デフォルトは `Random.default_rng()`)

## 例

```julia
# ガウス型トランジオグラムによるシミュレーションされたクエンチング
Quenching(GaussianTransiogram())

# ドメインの最初のジオメトリで値を変更しない
Quenching(SphericalTransiogram(), skip=[1])
```

## 参考文献

  * Carle et al 1998. [Conditional Simulation of Hydrofacies Architecture: A Transition Probability/Markov Approach](https://doi.org/10.2110/sepmcheg.01.147)
