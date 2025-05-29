```
@lazy import PkgName=UUID
```

パッケージ `PkgName` を遅延インポートし、実際の読み込みは最初の使用時に遅延されます。

```julia
module MyLazyPkg
    @lazy import Plots="91a5bcdd-55d7-5caf-9e0b-520d859cae80"
    draw_figure(data) = Plots.plot(data, title="MyPkg Plot")
end
```
