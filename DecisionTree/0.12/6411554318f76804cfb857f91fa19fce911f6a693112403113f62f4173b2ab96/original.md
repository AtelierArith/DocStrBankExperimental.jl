```
print_tree([io::IO,] tree::Node, depth=-1, indent=0; sigdigits=4, feature_names=nothing)
```

Print a textual visualization of the specified `tree`. For example, if for some input pattern the value of "Feature 3" is "-30" and the value of "Feature 2" is "100", then, according to the sample output below, the majority class prediction is 7. Moreover, one can see that of the 10555 training samples that terminate at the same leaf as this input data, 2493 of these predict the majority class, leading to a probabilistic prediction for class 7 of `2493/10555`. Ratios for non-majority classes are not shown.

# Example output:

```
Feature 3 < -28.15 ?
├─ Feature 2 < -161.0 ?
   ├─ 5 : 842/3650
   └─ 7 : 2493/10555
└─ Feature 7 < 108.1 ?
   ├─ 2 : 2434/15287
   └─ 8 : 1227/3508
```

To facilitate visualisation of trees using third party packages, a `DecisionTree.Leaf` object, `DecisionTree.Node` object or  `DecisionTree.Root` object can be wrapped to obtain a tree structure implementing the AbstractTrees.jl interface. See  [`wrap`](@ref)` for details.
