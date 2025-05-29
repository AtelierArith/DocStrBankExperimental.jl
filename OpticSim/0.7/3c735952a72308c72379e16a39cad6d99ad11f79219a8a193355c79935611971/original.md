```
Surface{T<:Real}
```

`T` is the number type used to represent the surface, e.g., `Float64`. Basic `Surface`s are *not* valid CSG objects, they function only in a stand-alone capacity.

**Must** implement the following:

```julia
surfaceintersection(surface::Surface{T}, ray::AbstractRay{T,3}) -> Union{EmptyInterval{T},Interval{T}}
normal(surface::Surface{T}) -> SVector{3,T}
interface(surface::Surface{T}) -> OpticalInterface{T}
makemesh(surface::Surface{T}) -> TriangleMesh{T}
```

In a conventional ray tracer the surface intersection function would only return the first surface the ray intersects. Because our ray tracer does CSG operations the surface intersection function intersects the ray with all leaf surfaces which are part of the CSG tree. 

Each leaf surface returns one or more 1D intervals along the ray. These intervals contain the part of the ray which is inside the surface. The intervals computed at the leaves are propagated upward through the CSG tree and the CSG operations of union, intersection, and difference are applied to generate new intervals which are themselves propagated upward.

The result is a union of 1D intervals, which may be disjoint, a single interval, or empty. The union of intervals represents the parts of the ray which are inside the CSG object.

Inside is well defined for halfspaces such as cylinders and spheres which divide space into two parts, but not for Bezier or NURBS patches which generally do not enclose a volume.  For surfaces which are not halfspaces the notion of inside is defined locally by computing the angle between the incoming ray and the normal of the surface at the point of intersection. All surfaces must be defined so that the normal points to the outside of the surface. 

A negative dot product between the incoming ray and the normal indicates the ray is coming from the outside of the surface and heading toward the inside. A positive dot product indicates the ray is coming from the inside of the surface and heading toward the outside.

Intervals are defined along the ray which is being intersected with the surface, so they are one dimensional. For example, assume we have a ray with origin o on the outside of a plane and an intersection with the plane at point int = o + td where t is a scalar and d is the unit direction of the ray. The inside interval will be (Intersection(t),Infinity). This interval begins at the intersection point on the plane and continues to positive infinity. The Intersection struct stores both the parametric value t and the 3D point of intersection to make various operations more efficient. But the interval operations only depend on the parametric value t.

If the origin o is on the inside of the plane then the inside interval will be (RayOrigin,Intersection(t)). Only the part of the ray from the ray origin to the intersection point is inside the plane. 

It is the programmer's responsibility to return Interval results from surfaceintersection that maintain these properties.

The following must be implemented only if the surface is being used as a detector

```julia
uv(surface::Surface{T}, p::SVector{3,T}) -> SVector{2,T}
uvtopix(surface::Surface{T}, uv::SVector{2,T}, imsize::Tuple{Int,Int}) -> Tuple{Int,Int}
onsurface(surface::Surface{T}, p::SVector{3,T}) -> Bool
```
