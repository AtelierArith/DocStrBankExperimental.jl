```
Problem(dev::Device=CPU(), advecting_flow; parameters...)
```

定常または時間変化する `advecting_flow` を持つ定常拡散問題をデバイス `dev` 上に構築します。デフォルトのデバイスは `CPU()` であり、`GPU` を使用するには関数に引数を渡します。問題の次元は提供された `advecting_flow` の型から推測されます：

  * `advecting_flow::OneDAdvectingFlow` は 1D 伝播-拡散問題用、
  * `advecting_flow::TwoDAdvectingFlow` は 2D 伝播-拡散問題用、
  * `advecting_flow::ThreeDAdvectingFlow` は 3D 伝播-拡散問題用。
