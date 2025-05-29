Return a new stock flow with flattened names, operators and positions from an AbstractStockAndFlowStructureF. Need to provide dynamic variable definitions, eg

```julia
convertSystemStructureToStockFlow(MyStockFlowStructure, (:v_prevalence=>(:I,:N,:/),:v_meanInfectiousContactsPerS=>(:c,:v_prevalence,:*)))
```
