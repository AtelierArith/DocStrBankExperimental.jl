```
BoundaryValueDiffEqAscher.Ascher1(; nlsolve = NewtonRaphson(), max_num_subintervals = 3000)
```

1段階ガウス・レジェンドルコレクション法で、アッシャーの実装から適応性を持たせています。

## キーワード引数

  * `nlsolve`: 内部非線形ソルバー。SciML `NonlinearProblem` インターフェースに準拠する任意のソルバーを使用できます。ソルバーの自動微分引数は無視され、カスタムヤコビアンアルゴリズムが使用されます。
  * `max_num_subintervals`: 最大サブインターバル数、デフォルトは3000です。
  * `zeta`: サイド条件ポイント、常に提供する必要があります。

!!! note
    型の安定性のために、`BVPJacobianAlgorithm` のForwardDiff ADTypesのチャンクサイズを提供する必要があります。


## 参考文献

```bibtex
@article{Ascher1994CollocationSF,
    title={Collocation Software for Boundary Value Differential-Algebraic Equations},
    author={Uri M. Ascher and Raymond J. Spiteri},
    journal={SIAM J. Sci. Comput.},
    year={1994},
    volume={15},
    pages={938-952},
    url={https://api.semanticscholar.org/CorpusID:10597070}
}

@article{Ascher1979ACS,
    title={A collocation solver for mixed order systems of boundary value problems},
    author={Uri M. Ascher and J. Christiansen and Robert D. Russell},
    journal={Mathematics of Computation},
    year={1979},
    volume={33},
    pages={659-679},
    url={https://api.semanticscholar.org/CorpusID:121729124}
}
```
