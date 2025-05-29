`weightinfo(W)`

`W` は代数群 `𝐆` を記述するコクセター群のレコード、または `IypeIrred` です。この関数は `𝐆` の同型類型に依存せず（つまり、根系に依存する `refltype(W)` のみに依存します）、次のキーを持つ辞書を返します：

  * `:minusculeWeights` 最小重みで、基本重みのリストにおけるその位置として記述されます。非可約群の場合、重みは各可約成分における重みの和であり、その成分のリストとして表されます。一貫性のために、可約系の場合、重みは1要素のリストとして表されます。
  * `:minusculeCoweights` 最小コ重みで、最小重みと同様の方法で表されます。
  * `:decompositions` 各コ重みに対して、隣接基本群の生成子の指数のリストによって与えられる生成子の観点からの分解です。次のフィールドとともに、隣接基本群の群構造を明らかにすることを可能にします。
  * `:moduli` 基本群の生成子の順序のリストです。
  * `:AdjointFundamentalGroup` 拡張根基底の置換として与えられる隣接基本群の生成子のリストです。
  * `:CenterSimplyConnected` 𝐆 のユニバーサルカバーの中心を生成する半単純要素のリストです。
  * `:chosenAdaptedBasis` 根格子に適応した重み格子の基底です。基本重みの基底において、根格子は `C=transpose(cartan(W))` によって与えられます。 `:chosenAdaptedBasis` を指定する特性は、`C*chosenAdaptedBasis` のエルミート標準形がほぼスミス標準形であることです（対角であるが、対角成分はスミス標準形と比較して置換される可能性がある；非自明な成分は `:decompositions` によって示される基本群の生成子に対応する位置にあります）。

```julia-repl
julia> weightinfo(coxgroup(:A,2)*coxgroup(:B,2))
Dict{Symbol, Array} with 8 entries:
  :moduli                  => [3, 2]
  :minusculeWeights        => [[1, 3], [1], [2, 3], [2], [3]]
  :decompositions          => [[2, 1], [2, 0], [1, 1], [1, 0], [0, 1]]
  :highestroot             => [5, 7]
  :chosenAdaptedBasis      => [1 -1 0 0; 0 1 0 0; 0 0 1 0; 0 0 0 1]
  :minusculeCoweights      => [[1, 4], [1], [2, 4], [2], [4]]
  :CenterSimplyConnected   => Vector{Rational{Int64}}[[1//3, 2//3, 0, 0], [0, 0…
  :AdjointFundamentalGroup => [(1,12,2), (4,14)]
```
