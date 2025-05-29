```
seesaw(
    CG::Matrix,
    scenario::AbstractVecOrTuple,
    d::Integer,
    n_trials::Integer = 1;
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

コリンズ-ギシン表記法 `CG` を使用して二部ベール関数を最大化します。`scenario` は入力と出力の数を詳細に示すベクトルで、順序は [oa, ob, ia, ib] です。`d` は戦略の局所次元を決定する整数です。

`oa` = `ob` = 2 の場合、ヒューリスティックは一連の固有値問題に簡略化されます。それ以外の場合は半正定値計画が必要で、シーソーのアセンブラージュ版を使用します。

ヒューリスティックは `n_trials` 回実行され、最良の実行結果が出力されます。

参考文献:

  * Pál and Vértesi, [arXiv:1006.3032](https://arxiv.org/abs/1006.3032)
  * Tavakoli et al., [arXiv:2307.02551](https://arxiv.org/abs/2307.02551) (Sec. II.B.1)
