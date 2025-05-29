```
gen_code(
    fname,
    graph;
    priohelp = Dict{Symbol,Float64}(),
    lang = LangJulia(),
    funname = "dummy",
    precomputed_nodes = [:A],
)
```

Generates the code for the `graph` in the language specified in `lang` and writes it into the file `fname`. The string `funname` is the function name. Topological order of the nodes is comptued using [`get_topo_order`](@ref) and `priohelp` can be used to influence the order. The nodes listed in `precomputed_nodes` are viewed as inputs, and code to compute these nodes are not computed.

Currently supported languages: [`LangC_MKL`](@ref), [`LangC_OpenBLAS`](@ref), [`LangJulia`](@ref), [`LangMatlab`](@ref).
