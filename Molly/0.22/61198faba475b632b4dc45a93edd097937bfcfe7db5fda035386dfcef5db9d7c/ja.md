```
System(; <keyword arguments>)
```

シミュレーションされる物理システム。

シミュレーションや分析で使用されないプロパティは、デフォルト値のままにしておくことができます。最小限必要な引数は `atoms`、`coords`、および `boundary` です。`atoms` と `coords` は同じ長さである必要があり、`velocities` と `atoms_data` が提供されている場合も同様です。これは AtomsBase.jl の `AbstractSystem` のサブタイプであり、そこで説明されているインターフェースを実装しています。

# 引数

  * `atoms::A`: システム内の原子または原子の同等物。任意の型で構いませんが、GPUを使用する場合はビット型であるべきです。
  * `coords::C`: システム内の原子の座標。通常は2次元または3次元の `SVector` のベクトルです。
  * `boundary::B`: シミュレーションが行われる境界ボックス。
  * `velocities::V=zero(coords) * u"ps^-1"`: システム内の原子の速度。
  * `atoms_data::AD=[]`: 原子に関連する他のデータで、原子がビット型であることを可能にし、したがってGPUで動作します。
  * `topology::TO=nothing`: 同じ分子に属する原子など、システムに関するトポロジー情報。
  * `pairwise_inters::PI=()`: システム内のペアワイズ相互作用、すなわち、すべてまたはほとんどの原子ペア間の相互作用（例：静電気）。通常は `Tuple` です。
  * `specific_inter_lists::SI=()`: システム内の特定の相互作用、すなわち、特定の原子間の相互作用（例：結合や角度）。通常は `Tuple` です。
  * `general_inters::GI=()`: システム内の一般的な相互作用、すなわち、すべての原子を含む相互作用（例：暗黙の溶媒）。各々は AtomsCalculators.jl インターフェースを実装する必要があります。通常は `Tuple` です。
  * `constraints::CN=()`: システム内の結合や角度に関する制約。通常は `Tuple` です。
  * `neighbor_finder::NF=NoNeighborFinder()`: 近くの原子を見つけて計算を節約するために使用される隣接原子探索器。
  * `loggers::L=()`: シミュレーション中に関心のあるプロパティを記録するロガー。
  * `force_units::F=u"kJ * mol^-1 * nm^-1"`: システムの力の単位。単位を使用しない場合は `NoUnits` に設定するべきです。
  * `energy_units::E=u"kJ * mol^-1"`: システムのエネルギーの単位。単位を使用しない場合は `NoUnits` に設定するべきです。
  * `k::K=Unitful.k` または `Unitful.k * Unitful.Na`: ボルツマン定数で、一部のシミュレーションで変更される場合があります。`k` は与えられた `energy_units` に基づいて選択されます。
  * `data::DA=nothing`: システムに関連する任意のデータ。
