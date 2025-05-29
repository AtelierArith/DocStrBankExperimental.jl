```
ConfigBody(nbody::Int,nverts::Int,verts::Matrix{Float64},ρ::Float64)
```

Set up configuration information for the a single body in the body system. Here we assume that all bodies has the same shape if more than one body exists. A single body is an infinitely thin body in y direction. It must have polygon shape and is described in z-x space. For example if we describe a rectangle in z-x space, for 3d problem it's just fine. For 2d problem in x-y space, this rectangle has a projection  of a line in x-y space. The vertices local coordinates are described in clockwise direction as a convention.

## Fields

  * `nbody`: Number of bodies in total
  * `nverts`: Number of vertices for one body
  * `verts`: Polygon vertices coordinates starting from the left bottom vert and   going in clockwise direction. Each line describes the (z,x) coordinate of   this vertice. Usually the z-dimesion has unit length 1 for 2-d problem.
  * `ρ`: Density of this body in mass per area

## Body setup

```
     ^(y)
     |
     |----->(x)
    /
 (-z)
```
