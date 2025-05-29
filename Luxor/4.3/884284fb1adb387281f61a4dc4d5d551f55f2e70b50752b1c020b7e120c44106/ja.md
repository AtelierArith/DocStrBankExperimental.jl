```
crescent(pos, innerradius, outeradius;
    action=nothing,
    vertices=false,
    reversepath=false,
    steps = 30)
```

現在のx軸に沿った三日月形の多角形を作成し、現在のパスに追加します。内半径が0の場合、半円が得られます。

他に `crescent(pos1, innerradius, pos2, outeradius...)` も参照してください。

## 例

外半径200、内半径130の塗りつぶされた三日月形を作成します。

```julia
crescent(O, 130, 200, :fill) # または
crescent(O, 130, 200, action=:fill)
```

ストロークされた三日月形を作成します - 内半径0は半円を生成し、現在のパスに追加します。

```julia
crescent(O, 0, 200, :stroke) # または
crescent(O, 0, 200, action=:stroke)
```
