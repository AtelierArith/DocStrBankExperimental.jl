```
topic_tree(
    index::DocIndex, levels::AbstractVector{<:Union{Integer, AbstractString}};
    sorted::Bool = true)
```

Builds a topic tree from the `index` for the provided `levels`.  Levels must be present in the index, eg, run `build_cluster!` first.

# Arguments

  * `index::DocIndex`: The document index
  * `levels::AbstractVector{<:Union{Integer, AbstractString}}`: The levels to include in the tree, eg, `[4, 10, 20]` (they must be present in index.topic_levels)
  * `sorted::Bool`: Whether to sort the children by the number of documents in each topic. Defaults to `true`.

# Example

```julia

# Create topic tree for levels k=4, k=10, k=20
root = topic_tree(index, [4, 10, 20])

# Display it
print_tree(root)
# example output
# "All Documents (N: 10, Share: 100.0%, Level: root, Topic ID: 0)"
# ├─ "Topic1 (N: 5, Share: 50.0%, Level: 4, Topic ID: 1)"
# │  └─ "Topic1 (N: 5, Share: 50.0%, Level: 10, Topic ID: 1)"
# ...
# └─ "Topic2 (N: 5, Share: 50.0%, Level: 4, Topic ID: 2)"
#    └─ "Topic2 (N: 5, Share: 50.0%, Level: 10, Topic ID: 2)"
# ...
```
