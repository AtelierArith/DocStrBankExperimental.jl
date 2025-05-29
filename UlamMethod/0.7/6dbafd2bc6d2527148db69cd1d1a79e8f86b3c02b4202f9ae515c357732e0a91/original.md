```
struct HyperRectangle{Dim, M, CRS}
```

An extention of `Meshes` to dimensions greater than 3.

The extension is minimal and implements no methods and does not interface with CRS.

### Fields

  * `min`: The coordinates of the minimum of the HyperRectangle as an `NTuple`.
  * `max`: The coordinates of the maximum of the HyperRectangle as an `NTuple`.
  * `vertices`: `[min, max]`, required by `Meshes`.

### Constructor

```
HyperRectangle(min, max)
```
