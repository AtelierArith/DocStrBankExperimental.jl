```
rectlattice!(net::FastNet,dims, <keyword arguments>)
```

Create a rectangular lattice with given dimensions *dims*. 

The network in *net* is replaced with the new topology, that is a lattice specified by dims.   *dims* can be a number, in this case it indicates the number of nodes to be arranged into a 1D lattice.  Alternatively, *dims* can be a vector of Ints. In this case the dimension of the lattice is identical to the  length of *dims* and each element of *dims* specifies the length of the lattice in one of these dimensions. 

If there FastNet is not large enough to accomodate the desired number of nodes or links an argument error  will be thrown. 

Keyword arguments are 

  * periodic : If this argument is true the lattice is generated with periodic boundary conditions in all dimensions.  Alternatively a Vector of Bool of the same length as *dims* can be supplied. In this case the n'th argument of  the vector specifies if the lattice is periodic in the n'th dimension.
  * S : The state of the nodes. All nodes will be set to this state.

# Examples

```jldoctest
julia> using Fastnet

julia>  net=FastNet(2000,6000,2,[])
Network of 0 nodes and 0 links

julia> rectlattice!(net,[10,20,10],periodic=[true,false,true])
Network of 2000 nodes and 5900 links

julia> degreedist(net)
6-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.1
 0.9
```
