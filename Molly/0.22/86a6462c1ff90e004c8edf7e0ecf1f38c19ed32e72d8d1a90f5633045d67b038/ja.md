```
MollyCalculator(; <キーワード引数>)
```

AtomsCalculators.jl インターフェースで使用するための計算機です。

`neighbors` は、計算関数を呼び出す際にキーワード引数としてオプションで指定でき、複数回の呼び出しで隣接原子が同じ場合に計算を節約できます。同様に、`n_threads` を指定して計算関数を実行する際に使用するスレッドの数を決定できます。この計算機は、他のコンテキストで Molly を使用するために設計されています。Molly で別の計算機を使用したい場合は、[`System`](@ref) を作成する際に `general_inters` として指定できます。

現在、バイリアル計算には対応していません。`σ` や `ϵ` などの原子特性を使用することにも対応していません。

# 引数

  * `pairwise_inters::PI=()`: システム内のペアワイズ相互作用、すなわち、静電気などのすべてまたはほとんどの原子ペア間の相互作用。通常は `Tuple` です。
  * `specific_inter_lists::SI=()`: システム内の特定の相互作用、すなわち、結合や角度などの特定の原子間の相互作用。通常は `Tuple` です。
  * `general_inters::GI=()`: システム内の一般的な相互作用、すなわち、暗黙の溶媒など、すべての原子を含む相互作用。各相互作用は AtomsCalculators.jl インターフェースを実装する必要があります。通常は `Tuple` です。
  * `neighbor_finder::NF=NoNeighborFinder()`: 近くの原子を見つけて計算を節約するために使用される隣接原子探索器。
  * `force_units::F=u"kJ * mol^-1 * nm^-1"`: システムの力の単位。単位を使用しない場合は `NoUnits` に設定する必要があります。
  * `energy_units::E=u"kJ * mol^-1"`: システムのエネルギーの単位。単位を使用しない場合は `NoUnits` に設定する必要があります。
  * `k::K=Unitful.k` または `Unitful.k * Unitful.Na`: ボルツマン定数で、一部のシミュレーションで変更される場合があります。`k` は指定された `energy_units` に基づいて選択されます。
  * `dims::Integer=3`: システム内の次元数。

```
