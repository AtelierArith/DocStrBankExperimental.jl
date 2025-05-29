```
read_tree(
	nwk_filename::AbstractString;
	node_data_type=DEFAULT_NODE_DATATYPE,
    label,
    force_new_labels=false,
    check=true,
)
read_tree(io::IO; kwargs...)
```

Read Newick file and create a `Tree{node_data_type}` object from it. If the input file contains multiple Newick strings on different lines, the output is an array of `Tree` objects.

The call `node_data_type()` must return a valid instance of a subtype of `TreeNodeData`. You can implement your own subtypes, or see `?TreeNodeData` for already implemented ones. The default is `EmptyData`.

Use `force_new_labels=true` to force the renaming of all internal nodes. By default the tree will be assigned a label by calling `default_tree_label()`. This can be changed using the `label` argument.

If you have a variable containing a Newick string and want to build a tree from it, use `parse_newick_string` instead.

## Note on labels

The `Tree` type identifies nodes by their labels. This means that labels have to be unique. For this reason, the following is done when reading a tree:

  * if an internal node does not have a label, a unique one will be created of the form  `"NODE_i"`
  * if a node has a label that was already found before in the tree, a random identifier  will be appended to it to make it unique. Note that the identifier is created using  `randstring(8)`, unicity is technically not guaranteed.
  * if `force_new_labels` is used, a unique identifier is appended to node labels
  * if node labels in the Newick file are identified as confidence/bootstrap values, a random  identifier is appended to them, even if they're unique in the tree. See  `?TreeTools.isbootstrap` to see which labels are identified as confidence values.
