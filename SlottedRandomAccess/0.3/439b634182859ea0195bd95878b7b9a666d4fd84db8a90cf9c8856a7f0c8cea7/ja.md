```
plrs = extract_plr(sim::PLR_Simulation)
plr = extract_plr(p::Union{PLR_Simulation_Point,PLR_Result})
```

`PLR_Simulation` または単一の `PLR_Simulation_Point` または `PLR_Result` から PLR 値を (0 と 1 の間の数値として) 抽出します。

最初のケースでは、関数は `PLR_Simulation` オブジェクト内の各負荷点に対して要素を持つベクトルを返します。
