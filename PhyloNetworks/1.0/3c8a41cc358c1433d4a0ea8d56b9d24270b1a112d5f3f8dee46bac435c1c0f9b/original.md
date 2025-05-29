```
hardwiredclusterdistance(net1::HybridNetwork, net2::HybridNetwork, rooted::Bool)
```

Hardwired cluster distance between the topologies of `net1` and `net2`, that is, the number of hardwired clusters found in one network and not in the other (with multiplicity, see below).

If the 2 networks are trees, this is the Robinson-Foulds distance. If rooted=false, then both networks are considered as semi-directed.

Networks are assumed bicombining (each hybrid has exactly 2 parents, no more).

## Dissimilarity vs distance

This is *not* a distance per se on the full space of phylogenetic networks: there are pairs of distinct networks for which this dissimilarity is 0. But it is a distance on some classes of networks, such as the class of tree-child networks that are "normal" (without shortcuts), or the class of tree-child networks that can be assigned node ages such that hybrid edges have length 0 and tree edges have non-negative lengths. See [Cardona, Rossello & Valiente (2008)](https://doi.org/10.1016/j.mbs.2007.11.003), [Cardona, Llabres, Rossello & Valiente (2008)](https://doi.org/10.1109/TCBB.2008.70), and [Huson, Rupp, Scornavacca (2010)](https://doi.org/10.1017/CBO9780511974076).

## Example

```jldoctest
julia> net1 = readnewick("(t6,(t5,((t4,(t3,((t2,t1))#H1)),#H1)));");

julia> taxa = sort(tiplabels(net1)); # t1 through t6, sorted alphabetically

julia> # using PhyloPlots; plot(net1, showedgenumber=true);

julia> # in matrix below: column 1: edge number. last column: tree (10) vs hybrid (11) edge
       # middle columns: for 'taxa': t1,...t6. 1=descendant, 0=not descendant
       hardwiredclusters(net1, taxa)
6×8 Matrix{Int64}:
 13  1  1  1  1  1  0  10
 12  1  1  1  1  0  0  10
 10  1  1  1  1  0  0  10
  9  1  1  1  0  0  0  10
  8  1  1  0  0  0  0  11
  7  1  1  0  0  0  0  10

julia> net2 = readnewick("(t6,(t5,((t4,(t3)#H1),(#H1,(t1,t2)))));");

julia> hardwiredclusters(net2, taxa)
6×8 Matrix{Int64}:
 13  1  1  1  1  1  0  10
 12  1  1  1  1  0  0  10
  6  0  0  1  1  0  0  10
  5  0  0  1  0  0  0  11
 11  1  1  1  0  0  0  10
 10  1  1  0  0  0  0  10

julia> hardwiredclusterdistance(net1, net2, true) # true: as rooted networks
4
```

## What is a hardwired cluster?

Each edge in a network is associated with its *hardwired cluster*, that is, the set of all its descendant taxa (leaves). The set of hardwired cluster of a network is the set of its edges' hardwired clusters. The dissimilarity `d_hard` defined in [Huson, Rupp, Scornavacca (2010)](https://doi.org/10.1017/CBO9780511974076) is the number of hardwired clusters that are in one network but not in the other.

This implementation is a slightly more discriminative version of `d_hard`, where each cluster is counted with multiplicity and annotated with its edge's hybrid status, as follows:

  * External edges are not counted (they are tree edges to a leaf, shared by all phylogenetic networks).
  * A cluster is counted for each edge for which it's the hardwired cluster.
  * At a given hybrid node, both hybrid partner edges have the same cluster, so this cluster is only counted once for both partners.
  * A given cluster is matched between the two networks only if it's the cluster from a tree edge in both networks, or from a hybrid edge in both networks.

In the example above, `net1` has a shortcut (hybrid edge 11) resulting in 2 tree edges (12 and 10) with the same cluster {t1,t2,t3,t4}. So cluster {t1,t2,t3,t4} has multiplicity 2 in `net1`. `net2` also has this cluster, but only associated with 1 tree edge, so this cluster contributes (2-1)=1 towards the hardwired cluster distance between the two networks. The distance of 4 corresponds to these 4 clusters:

  * {t1,t2,t3,t4}: twice in net1, once in net2
  * {t3,t4}: absent in net1, once in net2
  * {t1,t2}: twice in net1 (from a hybrid edge & a tree edge), once in net2
  * {t3}: absent in net1 (because external edges are not counted), once in net2 (from a hybrid edge).

Degree-2 nodes cause multiple edges to have the same cluster, so counting clusters with multiplicity distinguishes a network with extra degree-2 nodes from the "same" network after these nodes have been suppressed (e.g. with [`PhyloNetworks.fuseedgesat!`](@ref) or [`PhyloNetworks.shrinkedge!`](@ref)).

## Networks as semi-directed

If `rooted` is false and one of the phylogenies is not a tree (1+ reticulations), then all degree-2 nodes are removed before comparing the hardwired clusters, and the minimum distance is returned over all possible ways to root the networks at internal nodes.

See also: [`hardwiredclusters`](@ref), [`hardwiredcluster`](@ref)
