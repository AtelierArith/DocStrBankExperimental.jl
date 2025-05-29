```
DowkerComplex(A,maxdensity=1)

This returns the Dowker complex of a rectangular matrix A
Normal usage of this function should be

FS, GraphDensity=DowkerComplex(A);
or
FS, GraphDensity=DowkerComplex(A,maxdensity);

Here FS is of the type FiltrationOfSimplicialComplexes
And GraphDensity is an array of real numbers of length =F.depth
where each number GraphDensity[i] represents the graph density at the simplicial complex Δ_i in the filtration
```
