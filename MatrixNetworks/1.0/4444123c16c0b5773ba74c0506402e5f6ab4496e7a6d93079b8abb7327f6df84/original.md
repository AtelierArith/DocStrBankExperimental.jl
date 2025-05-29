  * triangles(A) return an iterator for all the triangles in a graph A
  * triangles(A,i) return an iterator for all triangles in a graph A involving node i
  * triangles(A,S) return an iterator for all triangles in a graph A involving a node in S
  * triangles(A,S;symmetries=true) return an iterator of all triangles in A involving a node in S with symmetries    (i.e. a triangle (i,j,k) is counted 6 times)

## sample run:

```
A = load_matrix_network("clique-10");
mytriangles = triangles(A)
for tri in mytriangles
    MatrixNetworks.triprint(tri)
end
z = collect(mytriangles)
ei,ej,ek = unzip_triangles(z)
```

## A quick example to access the first triangle:

```
julia> tri = first(mytriangles)
MatrixNetworks.tri_struct(1, 2, 3)

julia> tri.v1,tri.v2,tri.v3
(1, 2, 3)
```
