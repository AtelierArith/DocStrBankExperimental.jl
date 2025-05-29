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

指定された言語 `lang` で `graph` のコードを生成し、ファイル `fname` に書き込みます。文字列 `funname` は関数名です。ノードのトポロジカル順序は [`get_topo_order`](@ref) を使用して計算され、`priohelp` は順序に影響を与えるために使用できます。`precomputed_nodes` にリストされたノードは入力として見なされ、これらのノードを計算するコードは生成されません。

現在サポートされている言語: [`LangC_MKL`](@ref), [`LangC_OpenBLAS`](@ref), [`LangJulia`](@ref), [`LangMatlab`](@ref).
