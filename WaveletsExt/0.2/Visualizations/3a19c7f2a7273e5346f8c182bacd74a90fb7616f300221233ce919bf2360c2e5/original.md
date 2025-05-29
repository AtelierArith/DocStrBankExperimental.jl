```
plot_tfbdry!([plt], tree, [depth; start, node_color, line_color, background_color])
```

Given a tree, output a visual representation of the leaf nodes on top of the current plot object `plt`, user will have the option to start the node count of each level with 0 or 1.

# Arguments

  * `plt::Plots.Plot`: Plot object.
  * `tree::BitVector`: Tree for plotting the leaf nodes. Comes in the form of a `BitVector`.
  * `depth::Integer`: (Default: `log2(length(tree)+1) |> Int`) Maximum depth to be displayed.

# Keyword Arguments

  * `start::Integer`: (Default: `0`) Whether to zero-index or one-index the root of the tree.
  * `node_color::Symbol`: (Default: `:black`) Color of the leaf nodes.
  * `line_color::Symbol`: (Default: `:black`) Color of lines in plot.
  * `background_color::Symbol`: (Default: `:white`) Color of background.

# Returns

`::Plots.Plot`: Plot object with the visual representation of the leaf nodes.

# Examples

```julia
using Wavelets, WaveletsExt

# Build a tree using Wavelets `maketree`
tree = maketree(128, 7, :dwt)

# Plot the leaf nodes
plot_tfbdry!(tree)
```

**See also:** [`plot_tfbdry`](@ref), [`plot_tfbdry2`](@ref)
