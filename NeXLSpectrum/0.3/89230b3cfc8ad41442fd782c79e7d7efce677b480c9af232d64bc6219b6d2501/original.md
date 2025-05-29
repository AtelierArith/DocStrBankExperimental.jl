`AbstractWindow` is the base type for `TabulatedWindow`, `ModeledWindow` and `NoWindow`. You can view the window transmission function using `Gadfly` and the method:

```
plot(wind::Union{AbstractWindow, AbstractArray{<:AbstractWindow}}; xmax=20.0e3, angle=π/2, style=NeXLSpectrumStyle)
```

Window types are identified by types based on `WindowType` like `MoxtekAP33`, `MoxtekAP5`, `AmptekC1`, `AmptekC2`, `BerylliumWindow`.

An implementation of an `AbstractWindow` is instantiate using code like `TabulatedWindow(MoxtekAP33())` or `ModeledWindow(AmptekC1())`. In addition, there is a `NoWindow()` type that implements a 100% transparent window.

`AbstractWindow` types primarily implement `NeXLCore.transmission(wnd::AbstractWindow, energy::Float64, angle::Float64 = π / 2)`
