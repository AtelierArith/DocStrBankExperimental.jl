```
MultiPhaseCompositionalSystemLV(equation_of_state)
MultiPhaseCompositionalSystemLV(equation_of_state, phases = (LiquidPhase(), VaporPhase()); reference_densities = ones(length(phases)), other_name = "Water")
```

与えられた `equation_of_state` から `MultiComponentFlash` のための組成系を設定します。2つまたは3つの相が提供されている場合、液体または蒸気相でない相は、後続のシミュレーションで不混和として扱われ、成分としてリストされる際には `other_name` から名前が付けられます。
