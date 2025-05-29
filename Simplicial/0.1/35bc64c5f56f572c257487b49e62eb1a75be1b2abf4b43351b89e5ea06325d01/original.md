This function computes the combinatorial Laplacians in dimensions k=0,..,maxdim for any graded poset P.

Possible Usage:

Laps=Laplacians(Δ); # where Δ is a simplicial complex Laps=Laplacians(P); # where P is a graded poset Laps=Laplacians(D); # where D is a directed complex 

Here Laps[d+1] is the laplacian acting on the d-dimensional chains, starting with dimension d=0. Note that the returned matrices  Laps[d+1]  are sparse and integer-valued.  The combinatorial Laplaciansare computed for *non-reduced" (co-) homology operators
