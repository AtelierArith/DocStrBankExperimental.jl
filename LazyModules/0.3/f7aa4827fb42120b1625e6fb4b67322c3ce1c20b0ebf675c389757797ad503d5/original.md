```
@lazy import PkgName=UUID
```

Lazily import package `PkgName` with the actual loading delayed to the first usage.

```julia
module MyLazyPkg
    @lazy import Plots="91a5bcdd-55d7-5caf-9e0b-520d859cae80"
    draw_figure(data) = Plots.plot(data, title="MyPkg Plot")
end
```
