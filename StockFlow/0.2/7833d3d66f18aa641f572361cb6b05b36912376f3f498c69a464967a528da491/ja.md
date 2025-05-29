新しいストックフローを、AbstractStockAndFlowStructureFからフラット化された名前、演算子、位置を持つ形で返します。動的変数定義を提供する必要があります。例えば、

```julia
convertSystemStructureToStockFlow(MyStockFlowStructure, (:v_prevalence=>(:I,:N,:/),:v_meanInfectiousContactsPerS=>(:c,:v_prevalence,:*)))
```
