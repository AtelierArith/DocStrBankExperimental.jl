```
seitz(op::SymOperation) --> String
```

Computes the correponding Seitz notation for a symmetry operation in triplet/xyzt form.

Implementation based on ITA5 Table 11.2.1.1, with 3D point group parts inferred from the trace and determinant of the matrix $\mathb{W}$ in the triplet $\{\mathbf{W}|\mathbf{w}\}$.

| detW/trW |  -3 |  -2 |  -1 |   0 |   1 |   2 |   3 |
|:-------- | ---:| ---:| ---:| ---:| ---:| ---:| ---:|
| **1**    |     |     |   2 |   3 |   4 |   6 |   1 |
| **-1**   |  -1 |  -6 |  -4 |  -3 |   m |     |     |

with the elements of the table giving the type of symmetry operation in in Hermann-Mauguin notation. The rotation axis and the rotation sense are computed following the rules in ITA6 Sec. 1.2.2.4(1)(b-c). See also .

Note that the orientation of the axis (i.e. its sign) does not necessarily match the orientation picked in Tables 1.4.2.1-5 of ITA6; it is a matter of (arbitrary) convention, and the conventions have not been explicated in ITA.

2D operations are treated by the same procedure, by elevation in a third dimension; 1D operations by a simple inspection of sign.
