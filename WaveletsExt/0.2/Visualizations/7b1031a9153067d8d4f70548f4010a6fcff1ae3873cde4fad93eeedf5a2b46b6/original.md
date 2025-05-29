```
plot_tfbdry2!([plt], tree, [n, m; line_color, background_color])
```

Given a quadtree, output the visual representation of the leaf nodes on top of current plot object `plt`.

# Arguments

  * `plt::Plots.Plot`: Plot object.
  * `tree::BitVector`: Tree for plotting the leaf nodes. Comes in the form of a `BitVector`.
  * `n::Integer`: Vertical size of signal.
  * `m::Integer`: Horizontal size of signal.

# Keyword Arguments

  * `line_color::Symbol`: (Default: `:black`) Color of lines in plot.
  * `background_color::Symbol`: (Default: `:white`) Color of background.

# Returns

`::Plots.Plot`: Plot object with the visual representation of the leaf nodes.

# Examples

```julia
using Wavelets, WaveletsExt

# Build a quadtree using Wavelets `maketree`
tree = maketree(128, 128, 7, :dwt)

# Plot the leaf nodes
plot_tfbdry2!(tree)
```

**See also:** [`plot_tfbdry2`](@ref), [`plot_tfbdry`](@ref)
