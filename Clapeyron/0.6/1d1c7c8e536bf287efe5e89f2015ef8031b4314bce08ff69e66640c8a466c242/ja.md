```
VT_diffusive_stability(model,V,T,z)::Bool
```

(V,T,z) ペアの拡散安定性を実行し、`true/false` を返します。`∂²A/∂n²` のすべての固有値が正であるかどうかをチェックします。eos 計算が失敗した場合は `false` を返します。これは通常、最大密度（`Clapeyron.lb_volume(model,T,z)` によって与えられる）よりも低い密度で評価する際に発生します。
