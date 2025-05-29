```
UniformLeafProbabilities(tree::AbstractTree)
```

Given a tree, this function returns a dictionary which maps nodes of the tree to probabilities, given that there is a uniform distribution over the leaf nodes

### Required Arguments

`tree` is the tree for which the probability distribution will be generated

### Example

```
probs = UniformLeafProbabilities(tree)
```
