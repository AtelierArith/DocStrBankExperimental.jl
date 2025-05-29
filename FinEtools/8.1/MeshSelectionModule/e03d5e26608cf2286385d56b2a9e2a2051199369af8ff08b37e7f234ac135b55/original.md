```
selectnode(fens::FENodeSet; kwargs...)
```

Select nodes using some criterion.

# Arguments

  * `v` = array of locations, one location per row
  * `kwargs` = pairs of keyword argument/value

## Selection criteria

### box

```
nLx = vselect(fens.xyz, box = [0.0 Lx  0.0 0.0 0.0 0.0], inflate = Lx/1.0e5)
```

The keyword 'inflate' may be used to increase or decrease the extent of the box (or the distance) to make sure some nodes which would be on the boundary are either excluded or included.

### distance

```
list = selectnode(fens.xyz; distance=1.0+0.1/2^nref, from=[0. 0.],
        inflate=tolerance);
```

Find all nodes within a certain distance from a given point.

### plane

```
candidates = selectnode(fens; plane = [0.0 0.0 1.0 0.0], thickness = h/1000)
```

The keyword `plane` defines the plane by its normal (the first two or three numbers) and its distance from the origin (the last number). Nodes are selected they lie on the plane,  or near the plane within the distance `thickness` from the plane. The normal is assumed to be of unit length; if it isn't already, it will be normalized internally.

### nearestto

```
nh = selectnode(fens; nearestto = [R+Ro/2, 0.0, 0.0] )
```

Find the node nearest to the location given.

### farthestfrom

```
nh = selectnode(fens; farthestfrom = [R+Ro/2, 0.0, 0.0] )
```

Find the node farthest from the location given.
