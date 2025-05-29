```
partition!(forest; kw...)
```

森林の四分木を分割します。デフォルトでは、これは森林のランクに沿って四分木を均等に分割します。

デフォルトでは、兄弟要素はランク間で分割されます。これは、`coarsen!`で粗くすることができず、MPI依存の粗くすることを引き起こす可能性があります。`allow_for_coarsening==true`の場合、兄弟四分木を同じランクに保持することでこれを回避します。

`weight(forest, treeid, quadrant)`コールバックを提供することができ（これは各四分木の`Float64`重みを与えます）、森林の重み付き分割を行います。

また、森林は[`LNodes`](@ref)を介してグローバルに番号付けされたノードを均等に分配するように分割することもできます。これは、`lnodes_degree`をノードの次数に設定することで行われます。これには、`ghost`で渡されない場合に作成される[`GhostLayer`](@ref)が必要です。

分割のためのキーワード引数（`kw...`）は次のとおりです：

  * `ghost = nothing`: [`LNodes`](@ref)による分割時に使用される[`GhostLayer`](@ref)。
  * `lnodes_degree = nothing`: これが次数に設定されている場合、[`LNodes`](@ref)に基づいて分割します。
  * `allow_for_coarsening = false`: `true`の場合、粗くすることができる兄弟グループが同じランクに集められます。
  * `weight = nothing`: 重み付き分割を行うために各四分木の`Float64`重みを与えるコールバック。

基礎となるp4est分割関数に関する詳細については、`@doc P4estTypes.P4est.p4est_partition_ext`、`@doc P4estTypes.P4est.p8est_partition_ext`、`@doc P4estTypes.P4est.p4est_partition_lnodes`、および`@doc P4estTypes.P4est.p8est_partition_lnodes`を参照してください。
