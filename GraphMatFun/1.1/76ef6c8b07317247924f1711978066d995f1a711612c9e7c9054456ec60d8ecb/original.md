```
function export_compgraph(
        graph,
    fname;
    order = get_topo_order(graph)[1],
    fun = "",
    dom = "",
    err = "",
    genby = "",
    descr = "",
    user = splitdir(homedir())[end],
)
```

Exports the graph to the file `fname` using the computation graph format (cgr). These kwargs are strings or values that are stored as comments in the file

  * `descr` of the graph
  * `fun` function it approximates
  * `dom` domain it approximates
  * `err` error in this domain
  * `genby` script that generated this file
  * `user` a username that created the file

These kwarg influence how the graph is stored:

  * `order` specifies an order the graph nodes are stored

CGR format:

Every line corresponds to a node / operation. The syntax is matlab compatible, although [`gen_code`](@ref) produces faster matlab code.

See also [`export_compgraph`](@ref).
