```
zero_joint(joint::Joint[;dimfcn=position_and_vel_dimension])
```

関節の状態の異なる側面に対してゼロのベクトルを作成します。これは引数 `dimfcn` に基づいています。デフォルトでは `position_and_vel_dimension` を使用し、関節の位置と加速から進める必要がある関節速度の部分に応じたサイズのゼロベクトルを作成します。代わりに `position_dimension`、`constrained_dimension`、`unconstrained_dimension`、または `exogenous_dimension` を使用することもできます。
