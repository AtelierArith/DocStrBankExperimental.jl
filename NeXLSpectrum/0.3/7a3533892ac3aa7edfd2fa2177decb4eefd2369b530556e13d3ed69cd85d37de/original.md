`WindowType` is the abstract type for models or types of X-ray windows.  These types distinguish between the window type and the implementation.  Often, there are both tabulated transmission functions from the vendor and calculated transmission functions based on the construction of the window. Use the `TabulatedWindow` or `ModeledWindow` to instantiate `AbstractWindow` which implements the `transmission(wnd::AbstractWindow, energy::Float64, angle::Float64 = π / 2)` method.

Predefined `WindowType`s are `MoxtekAP33`, `MoxtekAP5`, `AmptekC1`, `AmptekC2`, `BerylliumWindow`.
