```
lnodes(forest::Pxest; ghost = nothing, degree = 1)
```

`forest`のための並列ノード番号付けを構築します。ゴーストレイヤー`ghost`が提供されていない場合は、構築されます。

`degree > 0`は、次数`degree`のロボットノードが構築されることを示します。`degree < 0`は、境界オブジェクト（面、エッジ、コーナー）が番号付けされることを示します。

`@doc P4estTypes.P4est.p4est_lnodes_t`および`@doc P4estTypes.P4est.p8est_lnodes_t`を参照して、次数に基づく番号付けについての詳細な議論を確認してください。
