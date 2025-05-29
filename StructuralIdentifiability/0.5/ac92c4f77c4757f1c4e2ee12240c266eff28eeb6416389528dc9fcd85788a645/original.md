```
linear_compartment_model(graph; inputs = [], outputs = [], leaks = [])
```

Input: defines a linear compartment model with nodes numbered from 1 to `n` by

  * `graph` - and array of integer arrays representing the adjacency lists of the graph
  * `inputs` - array of input nodes
  * `outputs` - array of output nodes
  * `leaks` - array of sink nodes

Output:

  * the corresponding ODE system in a standard notation  (as, e.g., in [this paper](https://doi.org/10.1007/s11538-015-0098-0))

Example: Consider a bidirected cycle with four nodes. Its adjacency list can be written as follows:

```
[ [2, 4], [1, 3], [2, 4], [1, 3] ]
```

In the list above, the `i`-th element is a list of vertices to which there exists an edge from the vertex `i`. Now we can create a linear compartment model over this graph with the output at vertex 1, input at vertex 2, and leaks at vertices 3 and 4 as follows:

```jldoctest
julia> ode = linear_compartment_model([[2, 4], [1, 3], [2, 4], [1, 3]], outputs = [1], inputs = [2], leaks = [2, 3])
x1' = -x1*a_2_1 - x1*a_4_1 + x2*a_1_2 + x4*a_1_4
x3' = x2*a_3_2 - x3*a_2_3 - x3*a_4_3 - x3*a_0_3 + x4*a_3_4
x2' = x1*a_2_1 - x2*a_1_2 - x2*a_3_2 - x2*a_0_2 + x3*a_2_3 + u2
x4' = x1*a_4_1 + x3*a_4_3 - x4*a_1_4 - x4*a_3_4
y1 = x1
```
