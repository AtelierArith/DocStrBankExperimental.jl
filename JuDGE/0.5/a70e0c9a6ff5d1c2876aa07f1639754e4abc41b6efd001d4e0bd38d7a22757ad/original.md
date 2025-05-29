```
ConditionallyUniformProbabilities(tree::AbstractTree)
```

Given a tree, this function returns a dictionary which maps nodes of the tree to probabilities, given that there are conditionally uniform probabilities over the children of any node.

### Required Arguments

`tree` is the tree for which the probability distribution will be generated

### Example

```
probs = ConditionallyUniformProbabilities(tree)
```
