```
ReplicaSystem(; <keyword arguments>)
```

レプリカ交換シミュレーションにおけるレプリカのラッパーです。

各個別レプリカは [`System`](@ref) です。シミュレーションや分析で使用されないプロパティは、デフォルト値のままにしておくことができます。最小限必要な引数は `atoms`、`replica_coords`、`boundary` および `n_replicas` です。`atoms` と `replica_coords` の要素は同じ長さである必要があり、`atoms_data` と `replica_velocities` の要素も提供される場合は同様です。`replica_coords`、`replica_velocities`、`replica_loggers` および相互作用引数 `replica_pairwise_inters`、`replica_specific_inter_lists`、`replica_general_inters`、`replica_constraints` の要素数は `n_replicas` と等しくする必要があります。これは AtomsBase.jl の `AbstractSystem` のサブタイプであり、そこで説明されているインターフェースを実装しています。

[`CellListMapNeighborFinder`](@ref) と共に `ReplicaSystem` を使用する場合、レプリカのシミュレーションと隣接者ファインダーの両方に使用されるスレッド数は同じに設定する必要があります。これは、構築時に `nbatches=(min(n, 8), n)` を [`CellListMapNeighborFinder`](@ref) に渡すことで行うことができ、ここで `n` は各レプリカに使用されるスレッドの数です。

# 引数

  * `atoms::A`: システム内の原子または原子の同等物。任意の型で構いませんが、GPUを使用する場合はビット型であるべきです。
  * `replica_coords`: 各レプリカ内の原子の座標。
  * `boundary::B`: シミュレーションが行われるバウンディングボックス。
  * `n_replicas::Integer`: システムのレプリカの数。
  * `replica_velocities=[zero(replica_coords[1]) * u"ps^-1" for _ in 1:n_replicas]`: 各レプリカ内の原子の速度。
  * `atoms_data::AD`: 原子に関連する他のデータで、原子がビット型であることを可能にし、したがってGPUで動作します。
  * `topology::TO=nothing`: システムに関するトポロジー情報、すなわちどの原子が同じ分子に属するか（すべてのレプリカで同じ場合に使用）。これは、引数 `replica_topology` に値が渡されない場合にのみ使用されます。
  * `replica_topology=[nothing for _ in 1:n_replicas]`: 各レプリカのトポロジー情報。
  * `pairwise_inters=()`: システム内のペアワイズ相互作用、すなわちすべてまたはほとんどの原子ペア間の相互作用（すべてのレプリカで同じ場合に使用）。通常は `Tuple` です。これは、引数 `replica_pairwise_inters` に値が渡されない場合にのみ使用されます。
  * `replica_pairwise_inters=[() for _ in 1:n_replicas]`: 各レプリカのペアワイズ相互作用。
  * `specific_inter_lists=()`: システム内の特定の相互作用、すなわち結合や角度などの特定の原子間の相互作用（すべてのレプリカで同じ場合に使用）。通常は `Tuple` です。これは、引数 `replica_specific_inter_lists` に値が渡されない場合にのみ使用されます。
  * `replica_specific_inter_lists=[() for _ in 1:n_replicas]`: 各レプリカ内の特定の相互作用。
  * `general_inters=()`: システム内の一般的な相互作用、すなわち暗黙の溶媒など、すべての原子を含む相互作用（すべてのレプリカで同じ場合に使用）。各相互作用は AtomsCalculators.jl インターフェースを実装する必要があります。通常は `Tuple` です。これは、引数 `replica_general_inters` に値が渡されない場合にのみ使用されます。
  * `replica_general_inters=[() for _ in 1:n_replicas]`: 各レプリカの一般的な相互作用。
  * `constraints::CN=()`: システム内の結合や角度に関する制約（すべてのレプリカで同じ場合に使用）。通常は `Tuple` です。これは、引数 `replica_constraints` に値が渡されない場合にのみ使用されます。
  * `replica_constraints=[() for _ in 1:n_replicas]`: 各レプリカ内の結合や角度に関する制約。
  * `neighbor_finder::NF=NoNeighborFinder()`: 近くの原子を見つけて計算を節約するために使用される隣接者ファインダー。各レプリカに複製されます。
  * `replica_loggers=[() for _ in 1:n_replicas]`: シミュレーション中に興味のあるプロパティを記録する各レプリカのロガー。
  * `exchange_logger::EL=ReplicaExchangeLogger(n_replicas)`: レプリカの交換を記録するために使用されるロガー。
  * `force_units::F=u"kJ * mol^-1 * nm^-1"`: システムの力の単位。単位が使用されていない場合は `NoUnits` に設定する必要があります。
  * `energy_units::E=u"kJ * mol^-1"`: システムのエネルギーの単位。単位が使用されていない場合は `NoUnits` に設定する必要があります。
  * `k::K=Unitful.k` または `Unitful.k * Unitful.Na`: ボルツマン定数で、一部のシミュレーションで変更される可能性があります。`k` は与えられた `energy_units` に基づいて選択されます。
  * `data::DA=nothing`: レプリカシステムに関連する任意のデータ。

```
