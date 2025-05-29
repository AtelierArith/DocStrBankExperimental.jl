## DIRCLUSTERCOEFFS

```
compute clustering coefficients for a directed graph.
cc = dirclustercoeffs(A) returns the directed clustering coefficients
(which generalize the clustering coefficients of an undirected graph, 
and so calling this function on an undirected graph will produce the same
answer as clustercoeffs, but less efficiently.)

This function implements the algorithm from Fagiolo, Phys Rev. E. 
76026107 (doi:10:1103/PhysRevE.76.026107).  

(cc,cccyc,ccmid,ccin,ccout,nf) = dirclusteringcoeffs(A) returns different 
components of the clustering coefficients corresponding to cycles,
middles, in triangles, and out triangles.  See the manuscript for a 
description of the various types of triangles counted in the above metrics.
```

## Functions

  * (cc,cccyc,ccmid,ccin,ccout,nf) = dirclustercoeffs{T}(A::SparseMatrixCSC{T,Int64},weighted::Bool)
  * (cc,cccyc,ccmid,ccin,ccout,nf) = dirclustercoeffs{T}(A::SparseMatrixCSC{T,Int64})
  * (cc,cccyc,ccmid,ccin,ccout,nf) = dirclustercoeffs{T}(A::SparseMatrixCSC{T,Int64},weighted::Bool,normalized::Bool)

## Example

```
(A,xy,labels) = load_matrix_network_metadata("celegans")
(cc, cccyc, ccmid, ccin, ccout, nf) = dirclustercoeffs(A, true, true)
(maxval, maxind) = findmax(cc)
labels[maxind]
```
