```julia
struct DERelative{T<:DistributedFactorGraphs.InferenceVariable, P, D} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

相対因子に完全なODEソリューションを構築して、可能なセンサーデータを相対変換に凝縮しますが、パラメータ推定プロセスは流動的に保ちます。最初と2番目の変数が同じ次元で互換性のある多様体であると仮定し、ODEはすべての次元でXiからXi+1まで実行されます。内部状態ベクトルは、必要に応じて異なるドメインにデカップリングできます。

ノート

  * DifferentialEquations.jlに基づいています
  * `getSample`ステップは`solve(ODEProblem)`ステップを実行します。
  * `tspan`はオブジェクト構築時に変数から一度だけ取得されます。つまり、変更されたタイムスタンプを検出しません。
  * 通常の因子評価は、完全な次元`AbstractRelativeRoots`として行われ、基本的な線形差分です。

開発ノート

  * FIXME 1025を参照、`multihypo=`はまだ機能しません。
  * FIXME たくさんの統合と標準化が必要です。Manifolds.jlに関するRoME.jl #244を参照してください。
  * TODO 因子が2つのタイムゾーンにまたがる場合の処理はまだ行われていません。
