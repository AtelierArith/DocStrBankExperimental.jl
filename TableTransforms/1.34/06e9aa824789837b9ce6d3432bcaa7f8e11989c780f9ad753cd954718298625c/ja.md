```
KMedoids(k; tol=1e-4, maxiter=10, weights=nothing, rng=Random.default_rng())
```

`k`-メドイドアルゴリズムを使用して、テーブルの行にラベルを割り当てます。

平均距離のメドイドに対する相対変化が許容誤差 `tol` よりも小さい場合、または反復回数が最大反復回数 `maxiter` を超えた場合、反復アルゴリズムは中断されます。

オプションで、TableDistances.jl の基礎となるテーブル距離に影響を与える各列の `weights` の辞書を指定し、再現可能な結果を得るための乱数生成器 `rng` を指定できます。

## 例

```julia
KMedoids(3)
KMedoids(4, maxiter=20)
KMedoids(5, weights=Dict(:col1 => 1.0, :col2 => 2.0))
```

## 参考文献

  * Kaufman, L. & Rousseeuw, P. J. 1990. [Partitioning Around Medoids (Program PAM)](https://onlinelibrary.wiley.com/doi/10.1002/9780470316801.ch2)
  * Kaufman, L. & Rousseeuw, P. J. 1991. [Finding Groups in Data: An Introduction to Cluster Analysis](https://www.jstor.org/stable/2532178)
