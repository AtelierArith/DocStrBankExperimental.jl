```
InvertFlow(fo::FlowOp)
```

`fo`の逆のフロー演算子を作成します。

# 例

```julia
inv_tanh_flow = InvertFlow(TanhFlow(2))
```
