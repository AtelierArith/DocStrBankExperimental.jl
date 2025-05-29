```
InfoNode{S, T}
InfoLeaf{T}
```

These types are introduced so that additional information currently not present in  a `DecisionTree`-structure – namely the feature names and the class labels –  can be used for visualization. This additional information is stored in the attribute `info` of  these types. It is a `NamedTuple`. So it can be used to store arbitraty information,  apart from the two points mentioned.

In analogy to the type definitions of `DecisionTree`, the generic type `S` is  the type of the feature values used within a node as a threshold for the splits between its children and `T` is the type of the classes given (these might be ids or labels).

```
!!! note
You may only add lacking class labels. It's not possible to overwrite existing labels
with this mechanism. In case you want add class labels, the generic type `T` must 
be a subtype of `Integer`.
```
