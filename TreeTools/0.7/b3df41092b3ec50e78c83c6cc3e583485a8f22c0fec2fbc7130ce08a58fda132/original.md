```
prune!(tree, node; kwargs...)
prune!(tree, labels::AbstractArray)
prune!(tree, labels...)
```

Prune `node` from `tree`. `node` can be a label or a `TreeNode`. Return the subtree defined by `node` as a `Tree` object as well as the previous ancestor of `node`.

If a list of labels is provided, the MRCA of the corresponding nodes is pruned.

## kwargs

  * `remove_singletons`: remove singletons (internals with one child) in the tree after pruning. Default `true`.
  * `clade_only`: if a list of labels is provided, check that it corresponds to a clade before pruning. Default `true`.
  * `create_leaf`: if the ancestor of `r` has only one child (singleton), pruning `r`  will create a leaf. If `create_leaf == :warn`, this will trigger a warning. If  `create_leaf = false`, it will trigger an error. If `create_leaf = true`, then this  is allowed. Default: `:warn`.

## Example

```jldoctest
using TreeTools # hide
tree = parse_newick_string("(A:1.,(B:1.,(X1:0.,X2:0.)X:5.)BX:1.)R;")
prune!(tree, ["X1", "X2"])
map(label, nodes(tree))

# output

3-element Vector{String}:
 "B"
 "A"
 "R"
```
