```
Matcher(selector; first = false)
```

Create a new `Matcher` object that can be used to test whether a `Node` matches the `selector` or not. `Matcher` objects are callable and can be used as follows:

```julia
function find_first_node(root, selector)
    # Create the `Matcher` object once, then reuse in the loop.
    matcher = Matcher(selector)
    for node in AbstractTrees.PreOrderDFS(root)
        if matcher(node)
            return node
        end
    end
    return nothing
end
```

The `matcher` object has two callable methods. The first, shown above, returns `true` or `false` depending on whether the selector matches. The other method takes a first argument function `::Node -> Nothing` that is called when the selector matches.

The keyword argument `first::Bool` has the same behaviour as the `first` keyword provided by `query`. See that function's documentation for details.
