```
selectelem(fens::FENodeSet, fes::T; kwargs...) where {T<:AbstractFESet}
```

Select finite elements.

# Arguments

  * `fens` = finite element node set
  * `fes` = finite element set
  * `kwargs` = keyword arguments to specify the selection criteria

## Selection criteria

### facing

Select all "boundary" elements that "face" a certain direction.

```
exteriorbfl = selectelem(fens, bdryfes, facing=true, direction=[1.0, 1.0, 0.0]);
```

or

```
exteriorbfl = selectelem(fens, bdryfes, facing=true, direction=dout, dotmin = 0.99);
```

where

```
function dout(xyz)
    return xyz/norm(xyz)
end
```

and `xyz` is the location of the centroid  of  a boundary element. Here the finite element is considered "facing" in the given direction if the dot product of its normal and the direction vector is greater than `dotmin`. The default value for `dotmin` is 0.01 (this corresponds to  almost 90 degrees between the normal to the finite element  and the given direction).

This selection method makes sense only for elements that are  surface-like (i. e. for boundary mmeshes).

### label

Select elements based on their label.

```
rl1 = selectelem(fens, fes, label=1)
```

### box, distance

Select elements based on some criteria that their nodes satisfy.  See the function `selectnode()`.

Example: Select all  elements whose nodes are closer than `R+inflate` from the point `from`.

```
linner = selectelem(fens, bfes, distance = R, from = [0.0 0.0 0.0],
  inflate = tolerance)
```

Example:

```
exteriorbfl = selectelem(fens, bdryfes,
   box=[1.0, 1.0, 0.0, pi/2, 0.0, Thickness], inflate=tolerance);
```

### withnodes

Select elements whose nodes are in a given list of node numbers.

Example:

```julia
l = selectelem(fens, fes, withnodes = [13, 14])
```

### flood

Select all FEs connected together, starting from a given node. Connections through a vertex (node) are sufficient.

Example: Select all FEs connected together (Starting from node 13):

```julia
l = selectelem(fens, fes, flood = true, startnode = 13)
```

### Optional keyword arguments

Should we consider the element only if all its nodes are in?

  * `allin` = Boolean: if true, then all nodes of an element must satisfy

the criterion; otherwise  one is enough.

# Output

`felist` = list of finite elements from the set that satisfy the criteria
