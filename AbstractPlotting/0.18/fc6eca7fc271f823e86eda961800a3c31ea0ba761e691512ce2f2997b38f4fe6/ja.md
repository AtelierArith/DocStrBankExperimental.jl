```julia
axis3d(args; attributes...)

```

3次元OldAxisをプロットします。

## 属性

`AbstractPlotting.Axis3D`のOldAxis属性とそのデフォルトは次のとおりです：

```
    showaxis: (true, true, true)
    showgrid: (true, true, true)
    padding: 0.1
    visible: true
    ticks: 
        rotation: (-0.7071067811865475 + -0.0im + -0.0jm - 0.7071067811865476km, -4.371139e-8 + 0.0im + 0.0jm + 1.0km, -3.090861907263062e-8 + 3.090861907263061e-8im + 0.7071067811865475jm + 0.7071067811865476km)
        font: ("Dejavu Sans", "Dejavu Sans", "Dejavu Sans")
        ranges_labels: (AbstractPlotting.Automatic(), AbstractPlotting.Automatic())
        formatter: plain
        textcolor: (RGBA{Float32}(0.5f0,0.5f0,0.5f0,0.6f0), RGBA{Float32}(0.5f0,0.5f0,0.5f0,0.6f0), RGBA{Float32}(0.5f0,0.5f0,0.5f0,0.6f0))
        align: ((:left, :center), (:right, :center), (:right, :center))
        textsize: (5, 5, 5)
        gap: 3
    frame: 
        axiscolor: (:black, :black, :black)
        axislinewidth: (1.5, 1.5, 1.5)
        linewidth: (1, 1, 1)
        linecolor: (RGBA{Float32}(0.5f0,0.5f0,0.5f0,0.4f0), RGBA{Float32}(0.5f0,0.5f0,0.5f0,0.4f0), RGBA{Float32}(0.5f0,0.5f0,0.5f0,0.4f0))
    names: 
        axisnames: ("x", "y", "z")
        rotation: (-0.7071067811865475 + -0.0im + -0.0jm - 0.7071067811865476km, -4.371139e-8 + 0.0im + 0.0jm + 1.0km, -3.090861907263062e-8 + 3.090861907263061e-8im + 0.7071067811865475jm + 0.7071067811865476km)
        font: ("Dejavu Sans", "Dejavu Sans", "Dejavu Sans")
        textcolor: (:black, :black, :black)
        align: ((:left, :center), (:right, :center), (:right, :center))
        textsize: (6.0, 6.0, 6.0)
        gap: 3
    inspectable: false
    showticks: (true, true, true)
    scale: Float32[1.0, 1.0, 1.0]
```
