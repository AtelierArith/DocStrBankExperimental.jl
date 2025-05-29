````
GR is a universal framework for cross-platform visualization applications.
It offers developers a compact, portable and consistent graphics library
for their programs. Applications range from publication quality 2D graphs
to the representation of complex 3D scenes.

See https://gr-framework.org/julia.html for full documentation.

Basic usage:
```julia
using GR
GR.init() # optional
plot(
    [0, 0.2, 0.4, 0.6, 0.8, 1.0],
    [0.3, 0.5, 0.4, 0.2, 0.6, 0.7]
)
# GR.show() # Use if in a Jupyter Notebook
```
````
