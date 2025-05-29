```
ode_norm(u, t)
```

HairerとWannerの重み付きL2ノルムの実装で、OrdinaryDiffEq.jlにおける誤差ベースのステップサイズ制御に使用されます。この関数はMPIを認識し、Trixi.jlのMPI並列実行時にグローバルMPI通信を使用します。

MPI並列実行での誤差ベースのステップサイズ制御を使用する際には、この関数をキーワード引数 `internalnorm = ode_norm` としてOrdinaryDiffEq.jlの `solve` に渡す必要があります。

[ドキュメント](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)の「高度な適応ステップサイズ制御」セクションを参照してください。
