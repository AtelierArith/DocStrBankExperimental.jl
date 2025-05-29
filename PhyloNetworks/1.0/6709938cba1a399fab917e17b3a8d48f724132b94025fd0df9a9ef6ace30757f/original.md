```
nni!(uv::Edge, nummove::UInt8, nohybridladder::Bool, no3cycle::Bool)
```

Modify a network with a nearest neighbor interchange (NNI) around its edge `uv`. Return the information necessary to undo the NNI, or `nothing` if the move was not successful (such as if the resulting graph was not acyclic (not a DAG) or if the focus edge is adjacent to a polytomy). If the move fails, the network is not modified. `nummove` specifies which of the available NNIs is performed.

rooted-NNI options according to Gambette et al. (2017), fig. 8:

  * BB: 2 moves, both to BB, if directed edges. 8 moves if undirected.
  * RR: 2 moves, both to RR.
  * BR: 3 moves, 1 RB & 2 BRs, if directed. 6 moves if e is undirected.
  * RB: 4 moves, all 4 BRs.

The extra options are due to assuming a semi-directed network, whereas Gambette et al (2017) describe options for rooted networks. On a semi-directed network, there might be a choice of how to direct the edges that may contain the root, e.g. choice of e=uv versus vu, and choice of labelling adjacent nodes as α/β (BB), or as α/γ (BR).

`nohybridladder` = true prevents moves that would create a hybrid ladder in the network, that is, 2 consecutive hybrid nodes (one parent of the other). `no3cycle` = true prevents NNI moves that would make a 3-cycle, and assumes that the input network does not have any 2- or 3-cycles. If `no3cycle` is false, 3-cycles can be generated, but NNIs generating 2-cycles are prevented.

The edge field `ischild1` is assumed to be correct in the overall network (that is, in sync with the network's field `.rooti`).
