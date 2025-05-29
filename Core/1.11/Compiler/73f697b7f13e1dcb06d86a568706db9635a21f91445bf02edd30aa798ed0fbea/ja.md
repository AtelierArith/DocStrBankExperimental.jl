```
const VarTable = Vector{VarState}
```

ローカル変数を推論された型にマッピングする拡張ラティスは `AbstractLattice` として表されます。各インデックスは、各ローカル変数を識別する `SlotNumber` の `id` に対応しています。`InferenceState` は、フロー感度分析を可能にするために、各SSAステートメントで複数の `VarTable` を維持することに注意してください。
