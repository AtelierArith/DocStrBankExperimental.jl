```
Slice(x=(xmin, xmax), y=(ymin, ymax), z=(zmin, zmax))
Slice(lat=(latmin, latmax), lon=(lonmin, lonmax))
```

`x`の制限[`xmax`,`xmax`]、`y`の制限[`ymax`,`ymax`]、および`z`の制限[`zmin`,`zmax`]内のドメイン要素を長さ単位（デフォルトはメートル）で保持するか、`lat`の制限[`latmin`,`latmax`]および`lon`の制限[`lonmin`,`lonmax`]内の度単位で保持します。

## 例

```julia
Slice(x=(1000km, 3000km))
Slice(x=(1000km, 2000km), y=(2000km, 5000km))
Slice(lon=(0°, 90°))
Slice(lon=(0°, 45°), lat=(0°, 45°))
```
