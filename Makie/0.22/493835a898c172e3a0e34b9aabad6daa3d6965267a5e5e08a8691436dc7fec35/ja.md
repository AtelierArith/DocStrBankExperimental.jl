```
BezierPath(svg::AbstractString; fit = false, bbox = nothing, flipy = false, flipx = false, keep_aspect = true)
```

SVGパスコマンドの文字列を使用して`BezierPath`を構築します。[SVGパスコマンド](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/d#path_commands)は、最初に`MoveTo`、`LineTo`、`CurveTo`、`EllipticalArc`、および`ClosePath`オブジェクトに解析され、その後`BezierPath`コンストラクタに渡されます。

`fit === true`の場合、パスは原点を中心とした幅1の正方形に収まるようにスケーリングされます。さらに、`bbox`が特定の`Rect`に設定されている場合、パスはこの長方形に収まるように調整されます。パスを散布マーカーとして使用したい場合、通常は中心に配置され、他の散布マーカーに対して比較可能なサイズになるようにフィットさせるのが良いです。

`flipy === true`または`flipx === true`の場合、パスのそれぞれの次元が反転されます。Makieはy=0が下部にあり、yが上に増加する座標系を使用していますが、SVGではy=0が上部にあり、yが下に増加しますので、ほとんどのSVGパスでは`flipy = true`が必要になります。

`keep_aspect === true`の場合、パスはバウンディングボックスに収まるようにフィットし、その長い次元がフィットし、もう一方は元のアスペクト比を保持するようにスケーリングされます。`keep_aspect = false`を設定すると、パスの新しいバウンディングボックスはフィットしたものになりますが、これにより潰れた外観になる可能性があることに注意してください。

## 例

パスコマンド文字列から三角形の`BezierPath`を構築し、散布マーカーとして使用します：

```julia
str = "M 0,0 L 10,0 L 5,10 z"
bp = BezierPath(str, fit = true)
scatter(1:10, marker = bp, markersize = 20)
```
