```
hybridlambdaformat(net::HybridNetwork; prefix="I")
```

Output `net` as a string in the format that the [Hybrid-Lambda](https://github.com/hybridLambda/hybrid-Lambda) simulator expects, namely:

  * all internal nodes are named, including the root, with names that are unique and start with a letter.
  * hybrid nodes are written as `H6#γ1:length1` and `H6#γ1:length2` instead of `#H6:length1::γ1` and `#H6:length2::γ2` (note the samme γ value expected by Hybrid-Lambda)

This is a modified version of the [extended Newick](https://doi.org/10.1186/1471-2105-9-532) format.

Optional keyword argument `prefix`: must start with a letter, other than "H". Internal nodes are given names like "I1", "I2", etc. Existing internal non-hybrid node names are **replaced**, which is crucial if some of them don't start with a letter (e.g. in case node names are bootstrap values). See [`nameinternalnodes!`](@ref) to add node names.

# examples

```jldoctest
julia> net = readnewick("((a:1,(b:1)#H1:1::0.8):5,(#H1:0::0.2,c:1):1);");

julia> hybridlambdaformat(net) # net is unchanged here
"((a:1.0,(b:1.0)H1#0.8:1.0)I1:5.0,(H1#0.8:0.0,c:1.0)I2:1.0)I3;"

julia> # using PhyloPlots; plot(net, shownodenumber=true) # shows that node -2 is the root

julia> rotate!(net, -2)

julia> writenewick(net) # now the minor edge with γ=0.2 appears first
"((#H1:0.0::0.2,c:1.0):1.0,(a:1.0,(b:1.0)#H1:1.0::0.8):5.0);"

julia> hybridlambdaformat(net)
"((H1#0.2:0.0,c:1.0)I2:1.0,(a:1.0,(b:1.0)H1#0.2:1.0)I1:5.0)I3;"

julia> net = readnewick("((((B)#H1:::.6)#H2,((D,C,#H2:::0.8),(#H1,A))));"); # 2 reticulations, no branch lengths

julia> writenewick(net, round=true)
"(#H2:::0.2,((D,C,((B)#H1:::0.6)#H2:::0.8),(#H1:::0.4,A)));"

julia> hybridlambdaformat(net; prefix="int")
"(H2#0.2,((D,C,((B)H1#0.6)H2#0.2)int1,(H1#0.6,A)int2)int3)int4;"
```
