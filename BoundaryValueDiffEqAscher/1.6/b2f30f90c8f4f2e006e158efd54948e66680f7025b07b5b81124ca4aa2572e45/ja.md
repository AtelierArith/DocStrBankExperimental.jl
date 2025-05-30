```
BoundaryValueDiffEqAscher.Ascher3(; nlsolve = NewtonRaphson(), max_num_subintervals = 3000)
```

Ascherの実装から適応された適応性を持つ3次のガウス・レジェンドルコレクション法。

## キーワード引数

  * `nlsolve`: 内部非線形ソルバー。SciML `NonlinearProblem` インターフェースに準拠する任意のソルバーを使用できます。ソルバーの自動微分引数は無視され、カスタムヤコビアンアルゴリズムが使用されます。
  * `max_num_subintervals`: 最大サブインターバルの数、デフォルトは3000。
  * `zeta`: サイド条件ポイント、常に提供する必要があります。

!!! note
    型の安定性のために、`BVPJacobianAlgorithm`内のForwardDiff ADTypesのチャンクサイズを提供する必要があります。


## 参考文献

```bibtex
@article{Ascher1994CollocationSF,
    title={境界値微分代数方程式のためのコレクションソフトウェア},
    author={Uri M. Ascher and Raymond J. Spiteri},
    journal={SIAM J. Sci. Comput.},
    year={1994},
    volume={15},
    pages={938-952},
    url={https://api.semanticscholar.org/CorpusID:10597070}
}

@article{Ascher1979ACS,
    title={境界値問題の混合次数系のためのコレクションソルバー},
    author={Uri M. Ascher and J. Christiansen and Robert D. Russell},
    journal={数学の計算},
    year={1979},
    volume={33},
    pages={659-679},
    url={https://api.semanticscholar.org/CorpusID:121729124}
}
```
