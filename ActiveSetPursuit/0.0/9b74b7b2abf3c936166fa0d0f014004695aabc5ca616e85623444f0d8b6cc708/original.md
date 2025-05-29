````
```julia
asp_omp(A,B)```
Orthogonal matching pursuit for sparse 
```math 
Ax=b
```
Applies the orthogonal matching pursuit (OMP) algorithm to
estimate a sparse solution of the underdetermined system `Ax=b`.

(BP)   
```math 
\min_x  \|x\|_1  
```
subject to  
```math 
Ax = b.
```
````
