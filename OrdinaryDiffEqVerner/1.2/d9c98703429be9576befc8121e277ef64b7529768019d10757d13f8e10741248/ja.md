自動切り替えアルゴリズムで、(非剛性) `Vern9()` と `stiff_alg` の間を切り替えることができます。

```
AutoVern9(stiff_alg; kwargs...)
```

このメソッドは `AutoAlgSwitch(Vern9(), stiff_alg; kwargs...)` と同等です。剛性アルゴリズムにアクセスするには、`OrdinaryDiffEqRosenbrock` などの追加ライブラリをインストールする必要があるかもしれません。
