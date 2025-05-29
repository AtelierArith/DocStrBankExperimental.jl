```
D3Tree(children, <keyword arguments>)
```

Construct a tree to be displayed using D3 in a browser or ipython notebook, specifying structure with lists of children indices.

# Arguments

## Required

  * `children::Vector{Vector{Int}}`: List of children for each node. E.g.

    ```julia
    D3Tree([[2,3], [], [4], []])
    ```

    creates a tree with four nodes. Nodes 2 and 3 are children of node 1, and node 4 is the only child of node 3. Nodes 2 and 4 are childless.

## Keyword:

  * `text::Vector{String}` - text to appear under each node.
  * `tooltip::Vector{String}` - text to appear when hovering over each node.
  * `style::Vector{String}` - html style for each node.
  * `link_style::Vector{String}` - html style for each link.
  * `title::String` - html title.
  * `init_expand::Integer` - levels to expand initially.
  * `init_duration::Number` - duration of the initial animation in ms.
  * `svg_height::Number` - height of the svg containing the tree in px.
