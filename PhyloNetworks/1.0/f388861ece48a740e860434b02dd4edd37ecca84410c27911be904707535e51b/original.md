```
hybridclades_support(boot_net::Vector{HybridNetwork}, ref_net::HybridNetwork; rooted=false)
```

Match hybrid nodes in a reference network with those in an array of networks, like bootstrap networks or in a posterior sample of networks. All networks must be fully resolved, and on the same taxon set. If `rooted=true`, all networks are assumed to have been properly rooted beforehand. Otherwise, the origin of each hybrid edge is considered as an unrooted bipartition (default).

Two hybrid edges in two networks are said to match if they share the same "hybrid" clade (or recipient) and the same "donor clade", which is a sister to the hybrid clade in the network. Since a hybrid clade has 2 parent edges, it is sister to two clades simultaneously: one is its major sister (following the major hybrid edge with γ>0.5) and one is its minor sister (following the major hybrid edge with γ<0.5).

To calculate these hybrid and sister clades at a given hybrid node, all other hybrid edges are first removed from the network. Then, the hybrid clade is the hardwired cluster (descendants) of either hybrid edge and major/minor clade is the hardwired cluster of the sibling edge of the major/minor hybrid parent. If `rooted=false`, sister clades are considered as bipartitions.

Output:

1. a "node" data frame (see below)
2. an "edge" data frame (see below)
3. a "clade" data frame to describe the make up of all clades found as hybrids or sisters, starting with a column `taxa` that lists all taxa. All other columns correspond to a given clade and contain true/false values. `true` means that a given taxon belongs in a given clade. For a clade named `H1`, for instance, and if the data frame was named `cla`, the list of taxa in this clade can be obtained with `cla[:taxa][cla[:H1]]`.
4. an array of gamma values, with one row for each network in the sample and two columns (major/minor) for each hybrid edge in the reference network. If this hybrid edge was found in the sampled network (i.e. same hybrid and sister clades, after removal of all other hybrid nodes), its inheritcance gamma value is recorded here. Otherwise, the gamma entry is 0.0.
5. a vector with the number of each hybrid edge in the reference network, in the same order as for the columns in the array of gamma values above.

The "node" data frame has one row per clade and 9 columns giving:

  * `:clade`: the clade's name, like the taxon name (if a hybrid is a single taxon) or the hybrid tag (like 'H1') in the reference network
  * `:node`: the node number in the reference network. missing if the clade is not in this network.
  * `:hybridnode`: typically the same node number as above, except for hybrid clades in the reference network. For those, the hybrid node number is listed here.
  * `:edge`: number of the parent edge, parent to the node in column 2, if found in the ref network. missing otherwise.
  * `:BS_hybrid`: percentage of sample networks in which the clade is found to be a hybrid clade.
  * `:BS_sister`: percentage of sample networks in which the clade is found to be sister to some hybrid clade (sum of the next 2 columns)
  * `:BS_major_sister`: percentage of sample networks in which the clade is found to be the major sister to some hybrid clade
  * `:BS_minor_sister`: same as previous, but minor
  * `:BS_hybrid_samesisters`: percentage of sample networks in which the clade is found to be a hybrid and with the same set of sister clades as in the reference network. Applies to hybrid clades found in the reference network only, missing for all other clades.

The "edge" data frame has one row for each pair of clades, and 8 columns:

  * `:edge`: hybrid edge number, if the edge appears in the reference network. missing otherwise.
  * `:hybrid_clade`: name of the clade found to be a hybrid, descendent of 'edge'
  * `:hybrid`: node number of that clade, if it appears in the reference network. missing otherwise.
  * `:sister_clade`: name of the clade that is sister to 'edge', i.e. be sister to a hybrid
  * `:sister`: node number of that clade, if in the ref network.
  * `:BS_hybrid_edge`: percentage of sample networks in which 'edge' is found to be a hybrid  edge, i.e. when the clade in the 'hybrid' column is found to be a hybrid and the clade in  the 'sister' column is one of its sisters.
  * `:BS_major`: percentage of sample networks in which 'edge' is found to be a major hybrid  edge, i.e. when 'hybrid' is found to be a hybrid clade and 'sister' is found to be its  major sister.
  * `:BS_minor`: same as previous, but minor
