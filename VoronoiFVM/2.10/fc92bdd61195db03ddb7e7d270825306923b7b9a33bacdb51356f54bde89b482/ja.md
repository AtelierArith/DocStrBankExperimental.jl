```julia
mutable struct TransientSolution{T, N, A, B} <: VoronoiFVM.AbstractTransientSolution{T, N, A, B}
```

一時的な解の構造体

## フィールド

  * `u::Any`: 解のベクトル
  * `t::Any`: 時間のベクトル
  * `history::Union{VoronoiFVM.DiffEqHistory, VoronoiFVM.TransientSolverHistory}`: 履歴

## インターフェース

このタイプのオブジェクトは `AbstractDiffEqArray` インターフェースに準拠しています。インデックス付けと補間については [https://diffeq.sciml.ai/stable/basics/solution/](https://diffeq.sciml.ai/stable/basics/solution/) を参照してください。

特に、一時的な解 `sol` は次のようにアクセスできます：

  * `sol[i]` はタイムステップ `i` の解を含みます
  * `sol[ispec,:,i]` はタイムステップ `i` における成分 `ispec` の解を含みます
  * `sol(t)` は `t` に対する（線形）補間された解の値を返します
  * `sol.t[i]` はタイムステップ `i` に対応する時間です
  * `sol[ispec,ix,i]` は時刻 `i` におけるノード `ix` での成分 `ispec` の解を指します
