```
create_gate_1q(gate_label::String, mat::Array{Complex{Float64},2})
```

新しいユーザー定義ゲートを作成し、生成行列をキャッシュし、回路で使用するためのGateOps.GateSymbolキーを返します。行列は内部的に2x2のStaticArrays SMatrixに変換されます。

# 例

```julia-repl

```
