```
constraints_list(ia::IntersectionArray)
```

Return the list of constraints of an intersection of a finite number of (polyhedral) sets.

### Input

  * `ia` – intersection of a finite number of (polyhedral) sets

### Output

The list of constraints of the intersection.

### Notes

We assume that the underlying sets are polyhedral, i.e., offer a method `constraints_list`.

### Algorithm

We create the polyhedron from the `constraints_list`s of the sets and remove redundant constraints.
