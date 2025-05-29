```
add_forward_trigger(n::JoinNode, from::AbstractReteNode)
```

adds `from` as a forward trigger of the JoinNode.

When a JoinNode `receive`s a fact from one of its forward trigger inputs, it joins that input with all combinations of facts from other inputs and performs its `join_function`.  Otherwise the JoinNode is not triggered.
