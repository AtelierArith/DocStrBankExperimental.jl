```
struct AnalyticalGeometry <: CSG.Geometry
  tree::Node
end
```

背景メッシュを切るために使用される解析幾何学を表す構造体です。

## コンストラクタ

```
AnalyticalGeometry(f::Function;name=string(nameof(f)))
```

ここで `f: Ω -> R` は、レベルセット関数に似ており、幾何学の内部では負、外部では正の値を持つ関数です。

## 事前定義された幾何学

```
doughnut(R,r;x0=zero(Point{3,typeof(R)}),name="doughnut")
popcorn(r0=0.6, σ=0.2, A=2, x0=zero(Point{3,typeof(r0)}), name="popcorn")
sphere(R;x0=zero(Point{3,eltype(R)}),name="sphere")
disk(R;x0=zero(Point{2,eltype(R)}),name="disk")
cylinder(R;x0=zero(Point{3,eltype(R)}),v=VectorValue(1,0,0),name="cylinder")
plane(x0=Point(0,0,0),v=VectorValue(1,0,0),name="plane")
square(L=1,x0=Point(0,0),name="square",edges=["edge_i" for i in 1:4])
quadrilateral(x0=Point(0,0),d1=VectorValue(1,0),d2=VectorValue(0,1),name="quadrilateral")
cube(L=1,x0=Point(0,0,0),name="cube")
tube(R,L;x0=zero(Point{3,typeof(R)}),v=VectorValue(1,0,0),name="tube")
olympic_rings(R,r,name="olympic_rings")
```
