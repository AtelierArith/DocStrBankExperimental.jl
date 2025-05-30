自動切り替えアルゴリズムで、(非剛性) `Vern7()` と `stiff_alg` の間で切り替えることができます。

```
AutoVern7(stiff_alg; kwargs...)
```

このメソッドは `AutoAlgSwitch(Vern7(), stiff_alg; kwargs...)` と同等です。剛性アルゴリズムにアクセスするには、`OrdinaryDiffEqRosenbrock` などの追加ライブラリをインストールする必要があるかもしれません。
