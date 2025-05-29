```
wrap(node::DecisionTree.Node, info = NamedTuple())
wrap(leaf::DecisionTree.Leaf, info = NamedTuple())
```

Add to each `node` (or `leaf`) the additional information `info`  and wrap both in an `InfoNode`/`InfoLeaf`.

Typically a `node` or a `leaf` is obtained by creating a decision tree using either the native interface of `DecisionTree.jl` or via other interfaces which are available for this package (like `MLJ`, ScikitLearn; see their docs for further details). Using the function `build_tree` of the native interface returns such an object. 

To use a DecisionTree `dc` (obtained this way) with the abstraction layer  provided by the `AbstractTrees`-interface implemented here and optionally add feature names `feature_names` and/or `class_labels`  (both: arrays of strings) use the following syntax:

1. `wdc = wrap(dc)`
2. `wdc = wrap(dc, (featurenames = feature_names, classlabels = class_labels))`
3. `wdc = wrap(dc, (featurenames = feature_names, ))`
4. `wdc = wrap(dc, (classlabels  = class_labels, ))`

In the first case `dc` gets just wrapped, no information is added. No. 2 adds feature names  as well as class labels. In the last two cases either of this information is added (Note the  trailing comma; it's needed to make it a tuple).
