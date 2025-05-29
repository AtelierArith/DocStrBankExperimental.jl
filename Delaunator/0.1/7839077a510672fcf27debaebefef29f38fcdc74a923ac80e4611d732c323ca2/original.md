```
clippedpoly(p::InfinitePolygon, bbox; [closed=true])
clippedpoly!(pts, p::InfinitePolygon, bbox)
```

returns an empty array if the poly is entirely outside the bounding box. Otherwise, return a set of points that represent edges of the infinite polygon clipped to the bounding box. The set of points will  be closed (where the first point is equal to the last) if the closed=true option is set. The set of points *may* be closed even if this isn't set. Using closed=true results in simpler behavior. This is not an option on the mutating version, see below for how to get this functionality.  

The mutating version will update the pts array by using

```
- `push!(pts, <newpt>)` 
- `last(pts)`
- `isempty(pts)`
```

It will return the input type pts. 

# Example code

```
# generate polygon regions for all of the dualcells 
# clipped to a 5% expansion of the point bounding box
# as a list of NaN separated paths, with all 
# polygons closed. 
using GeometryBasics
t = triangulate(rand(Point2f, 15))
ppts = Point2f[]
for i in eachindex(t)
    ind = lastindex(ppts)
    clippedpoly!(ppts, dualcell(t, i), margin_bbox(t, 0.05))
    # check if the polygon was closed... 
    if lastindex(ppts) > ind # then we added point
        if ppts[ind+1] != ppts[end] # check if we are closed
            push!(ppts, ppts[ind+1]) # close the polygon
        end 
    end 
    push!(ppts, (NaN,NaN)) # add the NaN separator 
end 
```

See also [`dualcell`](@ref). 
