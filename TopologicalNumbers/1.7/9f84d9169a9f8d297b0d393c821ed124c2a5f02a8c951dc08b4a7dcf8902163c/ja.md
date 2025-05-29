```
LBFSolution{T1,T2} <: TopologicalNumbersSolutions
```

`LBFSolution`構造体は、ベリーフラックスの$k$-ローカル値を計算するための解を表します。

# フィールド

  * `TopologicalNumber::T1`: 各エネルギーバンドのローカルベリーフラックス。
  * `n::T2`: ベリーフラックスを計算する際の波数($2\pi n/N$)を表す2つの`Int`要素を含む`AbstractVector`（または`Tuple`）。
