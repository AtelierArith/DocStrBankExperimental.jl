```
crescent(cp1, r1, cp2, r2;
    action=nothing,
    vertices=false,
    reversepath=false)
```

現在のx軸に沿った三日月形の多角形を作成するには、2つの円の交点を見つけて現在のパスに追加します。2つの中心位置は異なる必要があります。

`crescent(point, innerradius, outeradius...)` も参照してください。

## 例

2つの円から塗りつぶされた三日月形を作成します。

```julia
crescent(O, 100, O + (60, 0), 150, :fill) # または
crescent(O, 100, O + (60, 0), 150, action=:fill)
```
