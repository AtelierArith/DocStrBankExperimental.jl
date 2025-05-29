```
iterated_dominance_frontier(cfg::CFG, liveness::BlockLiveness, domtree::DomTree)
    -> phinodes::Vector{Int}
```

Run iterated dominance frontier. The algorithm we have here essentially follows LLVM, which itself is a a cleaned up version of the linear-time algorithm described in [^SG95].

The algorithm here is quite straightforward. Suppose we have a CFG:

```
A -> B -> D -> F
 \-> C ------>/
```

and a corresponding dominator tree:

```
A
|- B - D
|- C
|- F
```

Now, for every definition of our slot, we simply walk down the dominator tree and look for any edges that leave the sub-domtree rooted by our definition.

In our example above, if we have a definition in `B`, we look at its successors, which is only `D`, which is dominated by `B` and hence doesn't need a ϕ-node. Then we descend down the subtree rooted at `B` and end up in `D`. `D` has a successor `F`, which is not part of the current subtree, (i.e. not dominated by `B`), so it needs a ϕ-node.

Now, the key insight of that algorithm is that we have two defs, in blocks `A` and `B`, and `A` dominates `B`, then we do not need to recurse into `B`, because the set of potential backedges from a subtree rooted at `B` (to outside the subtree) is a strict subset of those backedges from a subtree rooted at `A` (out outside the subtree rooted at `A`). Note however that this does not work the other way. Thus, the algorithm needs to make sure that we always visit `B` before `A`.

[^SG95]: Vugranam C. Sreedhar and Guang R. Gao. 1995.      A linear time algorithm for placing φ-nodes.      In Proceedings of the 22nd ACM SIGPLAN-SIGACT symposium on Principles of programming languages (POPL '95).      Association for Computing Machinery, New York, NY, USA, 62–73.      DOI: [https://doi.org/10.1145/199448.199464](https://doi.org/10.1145/199448.199464).
