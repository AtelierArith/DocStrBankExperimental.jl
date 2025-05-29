```
deim(
    sys::ModelingToolkit.ODESystem,
    snapshot::AbstractMatrix,
    pod_dim::Integer;
    deim_dim::Integer = pod_dim,
    name::Symbol = Symbol(nameof(sys), :_deim),
    kwargs...
) -> ModelingToolkit.ODESystem
```

適切な直交分解（POD）を使用して、離散経験的補間法（DEIM）で `ModelingToolkit.ODESystem` を削減します。

`snapshot` は、各時間インスタンスのデータを列として持つ行列である必要があります。

`sys` の方程式の左辺はすべて1次導関数であると仮定されます。DEIMを適用する前に、`ModelingToolkit.ode_order_lowering` を使用して高次ODEを変換してください。

`sys` は内部システムを持たないと仮定されます。エンドユーザーは事前に `ModelingToolkit.structural_simplify` を呼び出すことを推奨します。

DEIM補間に使用されるPOD基底は、非線形項のスナップショット行列から取得され、非線形表現のために実行時に生成された関数を実行することで計算されます。
