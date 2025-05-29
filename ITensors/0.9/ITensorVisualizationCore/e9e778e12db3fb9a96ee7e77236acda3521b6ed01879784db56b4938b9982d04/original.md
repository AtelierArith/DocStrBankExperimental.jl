```
@visualize
```

Visualize a contraction of ITensors, returning the result of the contraction.

The contraction should be written in terms of a series of ITensors contracted with `*`.

# Examples

```julia
using ITensors
using ITensorUnicodePlots # Must load a backend or else no plots will be made

i = Index(2, "index_i")
j = Index(10, "index_j")
k = Index(40, "index_k")
l = Index(40, "index_l")
m = Index(40, "index_m")
A = random_itensor(i, j, k)
B = random_itensor(i, j, l, m)
C = random_itensor(k, l)

# Contract the tensors over the common indices
# and visualize the results
ABC = @visualize A * B * C

AB = @visualize A * B
# Use readline() to pause between plots
readline()
ABC = @visualize AB * C vertex_labels = ["A*B", "C"]
readline()

# Save the results to figures for viewing later
AB = @visualize fig1 A * B
ABC = @visualize fig2 AB * C vertex_labels = ["A*B", "C"]

display(fig1)
readline()
display(fig2)
readline()
```

# Keyword arguments:

  * `vertex_labels`: Custom tensor labels to display on the vertices of the  digram. If not specified, they are determined automatically from the input to the macro.
  * `edge_labels=IndexLabels()`: A list of the edge labels or an  `AbstractEdgeLabels` object specifying how they should be made.
  * `arrow_show`: Whether or not to show arrows on the edges.
