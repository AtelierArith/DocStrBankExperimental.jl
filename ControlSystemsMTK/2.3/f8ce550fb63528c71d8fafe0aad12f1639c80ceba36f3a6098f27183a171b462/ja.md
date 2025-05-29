```
ModelingToolkit.ODESystem(sys::AbstractStateSpace; name::Symbol, x0 = zeros(sys.nx), x_names, u_names, y_names)
```

`sys::StateSpace`からODESystemを作成します。

# 引数:

  * `sys`: `StateSpace`または`NamedStateSpace`のインスタンス。
  * `name`: システムにユニークな名前を付けるためのシンボル。
  * `x0`: 初期状態

以下の引数は、システムが`NamedStateSpace`の場合に自動的に設定されます。

  * `x_names`: 状態名のシンボルのベクトル。
  * `u_names`: 入力名のシンボルのベクトル。
  * `y_names`: 出力名のシンボルのベクトル。
