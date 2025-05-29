```
network_expectedCF(net::HybridNetwork; showprogressbar=true,
        inheritancecorrelation=0)
```

Calculate the quartet concordance factors (qCF) expected from the multispecies coalescent along network `net`. Output: `(q,t)` where `t` is a list of taxa, and `q` is a list of 4-taxon set objects of type `PhyloNetworks.QuartetT{datatype}`. In each element of `q`, `taxonnumber` gives the indices in `taxa` of the 4 taxa of interest; and `data` contains the 3 concordance factors, for the 3 unrooted topologies in the following order: `t1,t2|t3,t4`, `t1,t3|t2,t4` and `t1,t4|t2,t3`. This output is similar to that of `PhyloNetworks.countquartetsintrees` when 1 individual = 1 taxon, with 4-taxon sets listed in the same order (same output `t`, then same order of 4-taxon sets in `q`).

Assumption: the network should have **edge lengths in coalescent units**.

By default, lineages at a hybrid node come from a parent (chosen according to inheritance probabilities γ) *independently* across lineages. With option `inheritancecorrelation > 0`, lineages have positive dependence, e.g. to model locus-specific inheritance probabilities, randomly drawn from a Beta distribution with mean γ across all loci. If `inheritancecorrelation` is set to 1, then all lineages at a given locus inherit from the same (randomly sampled) parent. More generally, the lineages' parents are distributed according to a Dirichlet process with base distribution determined by the γ values, and with concentration parameter α = (1-r)/r, that is, r = 1/(1+α), where `r` is the input inheritance correlation.

# examples

```jldoctest
julia> using PhyloNetworks, QuartetNetworkGoodnessFit

julia> # network with 3_2 cycles, causing some anomalous quartets
       net = readTopology("(D:1,((C:1,#H25:0):0.1,((((B1:10,B2:1):1.5,#H1:0):10.8,((A1:1,A2:1):0.001)#H1:0::0.5):0.5)#H25:0::0.501):1);");

julia> # using PhyloPlots; plot(net, showedgelength=true);

julia> q,t = network_expectedCF(net); # anomalous: A1, A2, {B1 or B2}, {C or D}
Calculation quartet CFs for 15 quartets...
0+---------------+100%
  ***************

julia> show(q[1].taxonnumber)
[1, 2, 3, 4]
julia> show(q[1].data)
[0.8885456713760765, 0.05572716431196175, 0.05572716431196175]

julia> for qi in q
         println(join(t[qi.taxonnumber],",") * ": " * string(round.(qi.data, sigdigits=3)))
       end
A1,A2,B1,B2: [0.889, 0.0557, 0.0557]
A1,A2,B1,C: [0.168, 0.416, 0.416]
A1,A2,B2,C: [0.168, 0.416, 0.416]
A1,B1,B2,C: [0.0372, 0.0372, 0.926]
A2,B1,B2,C: [0.0372, 0.0372, 0.926]
A1,A2,B1,D: [0.168, 0.416, 0.416]
A1,A2,B2,D: [0.168, 0.416, 0.416]
A1,B1,B2,D: [0.0372, 0.0372, 0.926]
A2,B1,B2,D: [0.0372, 0.0372, 0.926]
A1,A2,C,D: [0.69, 0.155, 0.155]
A1,B1,C,D: [0.793, 0.103, 0.103]
A2,B1,C,D: [0.793, 0.103, 0.103]
A1,B2,C,D: [0.793, 0.103, 0.103]
A2,B2,C,D: [0.793, 0.103, 0.103]
B1,B2,C,D: [1.0, 9.42e-7, 9.42e-7]

```
