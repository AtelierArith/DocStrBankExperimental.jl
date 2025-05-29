```
adjacency!(net,mat;S=1)
```

Create a network with given adjacency matrix.

The network in *net* is replaced with the new topology that is specified by the adjacency matrix *mat*.  If direction of links matters note that the element *mat[i,j]* corresponds to the link from j to i. 

Symmeric matrices will not result in parallel links, instead the link is placed in an arbitrary direction. 

Note that node *n* in the matrix will be the node in position *n* in *net* after creation, which is  not necessarily the node with ID *n*, if you need to find a particular node at a later time then it is best to save its id using the node(net,pos) function directly after calling adjacency!(net,mat). 

If *net* is not large enough to accomodate the desired number of nodes or links an argument error  will be thrown. 

Keyword arguments are 

  * S : The state of the nodes. All nodes will be set to this state.

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> mat=[0 1 0; 1 0 1; 0 1 0]
3×3 Matrix{Int64}:
 0  1  0
 1  0  1
 0  1  0

julia> adjacency!(net,mat)
Network of 3 nodes and 2 links
```
