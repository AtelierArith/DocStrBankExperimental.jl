Node in a network

The `taxon` field is a `MangalReferenceTaxon` object, so that one can, for example, query the TSN identifier of a node through `object.taxon.tsn`.

This approach has been chosen because (i) names of nodes in networks can be non unique and (ii) nodes within the same networks can refer to various taxonomic levels. As an example, if a network has four distinct nodes identified as `Ascariasis sp.`, they will represent four nodes in the networks, but map onto the same `MangalReferenceTaxon` (representing the entire *Ascariasis* genus). This approach provides a seemless representation of the same taxon across different networks, but also of the same taxon *within* networks.
