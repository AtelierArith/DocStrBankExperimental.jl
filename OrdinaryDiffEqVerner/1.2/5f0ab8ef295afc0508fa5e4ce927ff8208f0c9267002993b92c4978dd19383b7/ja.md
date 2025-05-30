自動切り替えアルゴリズムで、(非剛性) `Vern8()` と `stiff_alg` の間で切り替えることができます。

```
AutoVern8(stiff_alg; kwargs...)
```

このメソッドは `AutoAlgSwitch(Vern8(), stiff_alg; kwargs...)` と同等です。剛性アルゴリズムにアクセスするには、`OrdinaryDiffEqRosenbrock` などの追加ライブラリをインストールする必要があるかもしれません。
