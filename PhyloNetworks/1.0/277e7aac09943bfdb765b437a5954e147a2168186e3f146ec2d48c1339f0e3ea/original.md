```
setgamma!(Edge, new γ, change_other=true)
```

Set inheritance probability γ for an edge, which must be a hybrid edge. The new γ needs to be in [0,1]. The γ of the "partner" hybrid edge is changed accordingly, to 1-γ. The field `ismajor` is also changed accordingly. If the new γ is approximately 0.5, `Edge` is set to the major parent, its partner is set to the minor parent.

If `net` is a HybridNetwork object, `printedges(net)` will show the list of edges and their γ's. The γ of the third hybrid edge (say) can be changed to 0.2 with `setgamma!(net.edge[3],0.2)`. This will automatically set γ of the partner hybrid edge to 0.8.

The last argument is true by default. If false: the partner edge is not updated. This is useful if the new γ is 0.5, and the partner's γ is already 0.5, in which case the `ismajor` attributes can remain unchanged.

See also [`PhyloNetworks.setmultiplegammas!`](@ref)
