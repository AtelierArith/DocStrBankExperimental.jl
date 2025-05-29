```
RectangularPrism(halfsizex::T, halfsizey::T, visheight::T=2.0; interface::NullOrFresnel{T} = nullinterface(T)) -> CSGGenerator{T}
```

Create an infinitely tall rectangular prism with axis `(0, 0, 1)`. For visualization `visheight` is used, **note that this does not fully represent the surface**.
