circleintersectionpts - Finds intersections of two circles.

Function computes the intersection points between two circles given their centres and radii.

```
Usage: (i1, i2) = circleintersectionpts(c1, r1, c2, r2, lr)
             i1 = circleintersectionpts(c1, r1, c2, r2, lr)

Arguments:
        c1, c2 - 2-vectors specifying the centres of the two circles.
        r1, r2 - Radii of the two circles.
            lr - Optional string specifying what solutions are wanted:
                "l" for the solution to the left of the line from c1 to c2
                "r" for the solution to the right of the line from c1 to c2
                "lr" if both solutions are wanted (default).

Returns:
     (i1, i2) - Tuple of 2D intersection points if both solutions requested.
          i1  - Single 2D intersection point if a single solution requested.
```

If no solution exists empty vectors are returned for i1, i2.  If the two circles are identical there are an infinite number of solutions. In this case we simply choose to subtract/add r1 in the x direction to c1 to obtain the 'left' and 'right' solutions.
