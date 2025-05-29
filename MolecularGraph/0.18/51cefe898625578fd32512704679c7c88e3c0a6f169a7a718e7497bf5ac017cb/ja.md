```
tdmcis(mol1::MolGraph, mol2::MolGraph; kwargs...) -> (Dict, Symbol)
tdmces(mol1::MolGraph, mol2::MolGraph; kwargs...) -> (Dict, Symbol)
```

mol1とmol2の間の非連結MCSをトポロジー制約付きで計算します（td-MCS）。

## キーワード引数

  * diameter(Int): トポロジー制約のための距離カットオフ。
  * tolerance(Int): トポロジー制約のための距離不一致許容値。
  * timeout(Real): 実行時間が指定された値（デフォルト=60秒）に達した場合、計算を中止し、最適でない結果を返します。
  * targetsize(Int): 指定されたMCSサイズが達成された場合、計算を中止し、これまでの最適でない結果を返します。

# 参考文献

1. Kawabata, T. (2011). Build-Up Algorithm for Atomic Correspondence between

Chemical Structures. Journal of Chemical Information and Modeling, 51(8), 1775–1787. https://doi.org/10.1021/ci2001023

1. https://www.jstage.jst.go.jp/article/ciqs/2017/0/2017*P4/*article/-char/en
