```
struct AnalyticalGeometry <: CSG.Geometry
  tree::Node
end
```

A structure to represent analytical geometries, used to cut background meshes.

## Constructor

```
AnalyticalGeometry(f::Function;name=string(nameof(f)))
```

where `f: Ω -> R` is a function that, similiarly to a level set function, is negative inside the geometry and positive outside.

## Predefined geometries

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
