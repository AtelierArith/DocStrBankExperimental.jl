`AbstractWindow`は`TabulatedWindow`、`ModeledWindow`、および`NoWindow`のベースタイプです。ウィンドウの透過関数は、`Gadfly`と次のメソッドを使用して表示できます。

```
plot(wind::Union{AbstractWindow, AbstractArray{<:AbstractWindow}}; xmax=20.0e3, angle=π/2, style=NeXLSpectrumStyle)
```

ウィンドウタイプは、`WindowType`に基づくタイプ（例：`MoxtekAP33`、`MoxtekAP5`、`AmptekC1`、`AmptekC2`、`BerylliumWindow`）によって識別されます。

`AbstractWindow`の実装は、`TabulatedWindow(MoxtekAP33())`や`ModeledWindow(AmptekC1())`のようなコードを使用してインスタンス化されます。さらに、100%透明なウィンドウを実装する`NoWindow()`タイプもあります。

`AbstractWindow`タイプは主に`NeXLCore.transmission(wnd::AbstractWindow, energy::Float64, angle::Float64 = π / 2)`を実装します。
