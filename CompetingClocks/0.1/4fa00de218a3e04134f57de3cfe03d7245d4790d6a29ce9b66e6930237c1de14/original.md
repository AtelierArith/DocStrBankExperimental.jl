```
DirectCall{KeyType,TimeType,TreeType}()
```

DirectCall is responsible for sampling among Exponential distributions. It samples using the Direct method. In this case, there is no optimization to that Direct method, so we call it DirectCall because it recalculates everything every time you call it.

The algorithm for the Direct Method relies heavily on what data structure it uses to maintain a list of hazard rates, such that it can know the sum of those hazards and index into them using a random value. This struct has a default constructor that chooses a data structure for you, but there are several options.

# Example

If we know that our simulation will only use a small number of different clock keys, then it would make sense to use a data structure that disables clocks by zeroing them out, instead of removing them from the list. This will greatly reduce memory churn. We can do that by changing the underlying data structure.

```julia
prefix_tree = BinaryTreePrefixSearch{T}()
keyed_prefix_tree = KeyedKeepPrefixSearch{K,typeof(prefix_tree)}(prefix_tree)
sampler_noremove = DirectCall{K,T,typeof(keyed_prefix_tree)}(keyed_prefix_tree)
```
