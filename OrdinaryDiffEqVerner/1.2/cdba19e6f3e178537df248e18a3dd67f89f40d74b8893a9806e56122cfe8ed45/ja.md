自動切り替えアルゴリズムで、(非剛性) `Vern6()` と `stiff_alg` の間で切り替えることができます。

```
AutoVern6(stiff_alg; kwargs...)
```

このメソッドは `AutoAlgSwitch(Vern6(), stiff_alg; kwargs...)` と同等です。剛性アルゴリズムにアクセスするには、`OrdinaryDiffEqRosenbrock` などの追加ライブラリをインストールする必要があるかもしれません。
