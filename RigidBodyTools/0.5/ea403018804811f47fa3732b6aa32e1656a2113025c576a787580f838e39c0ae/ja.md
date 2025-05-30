```
zero_joint(ls::RigidBodyMotion[;dimfcn=position_and_vel_dimension])
```

リンクされたシステム `ls` の状態のいくつかの側面に対してゼロのベクトルを作成します。これは引数 `dimfcn` に基づいています。デフォルトでは `position_and_vel_dimension` を使用し、ジョイントの状態に応じたサイズのゼロベクトルを作成します。代わりに `position_dimension`、`constrained_dimension`、`unconstrained_dimension`、または `exogenous_dimension` を使用することもできます。
