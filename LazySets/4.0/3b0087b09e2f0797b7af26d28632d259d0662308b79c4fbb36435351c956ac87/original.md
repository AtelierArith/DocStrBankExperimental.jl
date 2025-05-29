```
remove_redundant_constraints!(P::AbstractHPolygon)
```

Remove all redundant constraints of a polygon in constraint representation.

### Input

  * `P` – polygon in constraint representation

### Output

The same polygon with all redundant constraints removed.

### Notes

Since we only consider bounded polygons and a polygon needs at least three constraints to be bounded, we stop removing redundant constraints if there are three or fewer constraints left. Hence for unbounded polygons the result may be unexpected.

### Algorithm

We go through all consecutive triples of constraints and check if the one in the middle is redundant. For this we assume that the constraints are sorted.
