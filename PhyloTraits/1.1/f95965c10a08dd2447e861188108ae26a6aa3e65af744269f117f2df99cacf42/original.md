```
ancestralreconstruction(obj::SSM, trait::Integer = 1)
```

Estimate the marginal probability of ancestral states for discrete character number `trait` (first trait by default). The parameters of the [`StatisticalSubstitutionModel`](@ref) object `obj` must first be fitted using [`fitdiscrete`](@ref), and ancestral state reconstruction is conditional on the estimated parameters. If these parameters were estimated using all traits, they are used as is, to do ancestral state reconstruction of the particular `trait` of interest.

**output**: data frame with a first column for the node numbers, a second column for the node labels, and a column for each possible state: the entries in these columns give the marginal probability that a given node has a given state.

warnings:

  * node numbers and node labels refer to those in `obj.net`, which might have a different internal representation of nodes than the original network used to build `obj`.
  * `obj` is modified: its likelihood fields (forward, directional & backward) are updated to make sure that they correspond to the current parameter values in `obj.model`, and to the `trait` of interest.

limitations: the following are not checked.

  * Assumes that every node in the large network is also present (with descendant leaves) in each displayed tree. This is not true if the network is not tree-child...
  * Assumes that the root is also in each displayed tree, which may not be the case if the root had a hybrid child edge.

See also [`posterior_logtreeweight`](@ref) and [`discrete_backwardlikelihood_trait!`](@ref) to update `obj.backwardlik`.

# examples

```jldoctest
julia> net = readnewick("(((A:2.0,(B:1.0)#H1:0.1::0.9):1.5,(C:0.6,#H1:1.0::0.1):1.0):0.5,D:2.0);");

julia> m1 = BinaryTraitSubstitutionModel([0.1, 0.1], ["lo", "hi"]);

julia> using DataFrames

julia> dat = DataFrame(species=["C","A","B","D"], trait=["hi","lo","lo","hi"]);

julia> fit1 = fitdiscrete(net, m1, dat);

julia> asr = ancestralreconstruction(fit1)
9×4 DataFrame
 Row │ nodenumber  nodelabel  lo        hi
     │ Int64       String     Float64   Float64
─────┼───────────────────────────────────────────
   1 │          1  A          1.0       0.0
   2 │          2  B          1.0       0.0
   3 │          3  C          0.0       1.0
   4 │          4  D          0.0       1.0
   5 │          5  5          0.286021  0.713979
   6 │          6  6          0.319456  0.680544
   7 │          7  7          0.16855   0.83145
   8 │          8  8          0.767359  0.232641
   9 │          9  H1         0.782776  0.217224

julia> using PhyloPlots

julia> plot(fit1.net, nodelabel = asr[!,[:nodenumber, :lo]], tipoffset=0.2); # pp for "lo" state
```
