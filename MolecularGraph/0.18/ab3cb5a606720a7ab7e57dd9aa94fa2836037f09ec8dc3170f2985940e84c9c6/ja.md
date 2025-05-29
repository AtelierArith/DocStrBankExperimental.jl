```
disconnected_mcis(mol1::MolGraph, mol2::MolGraph; kwargs...) -> (Dict, Symbol)
disconnected_mces(mol1::MolGraph, mol2::MolGraph; kwargs...) -> (Dict, Symbol)
```

mol1とmol2の間の切断された最大共通部分構造（MCS）を計算します。

## キーワード引数

  * timeout(Real): 実行時間が指定された値に達した場合、計算を中止し、最適でない結果を返します（デフォルト=60秒）。
  * targetsize(Int): 指定されたMCSサイズが達成された場合、計算を中止し、これまでの最適でない結果を返します。
