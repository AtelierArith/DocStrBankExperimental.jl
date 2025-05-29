Plot a metabolic map that is compatible with Escher. The only required argument is the location of the metabolic map in `json` format.

# Example

```
escherplot("core-map.json"; kwargs...)
```

Here `kwargs` are supported attributes, see the `readme` for more information.

# Attributes

```
metabolite_identifier = "bigg_id"
metabolite_show_text = false
metabolite_text_size = 4
metabolite_primary_node_size = 5 # fallback size
metabolite_secondary_node_size = 3 # fallback size
metabolite_node_sizes = Dict{String,Any}()
metabolite_node_colors = Dict{String,Any}()
metabolite_node_color = :black # fallback color
metabolite_text_color = :black
reaction_identifier = "bigg_id"
reaction_show_text = false
reaction_show_name_instead_of_id = false
reaction_text_size = 4
reaction_text_color = :black
reaction_edge_colors = Dict{String,Any}() # actual color
reaction_edge_color = :black # fallback color
reaction_edge_widths = Dict{String,Any}() # actual edge width
reaction_edge_width = 2.0 # fallback width
reaction_arrow_size = 6
reaction_arrow_head_offset_fraction = 0.1 # between 0 and 1
reaction_directions = Dict{String,Tuple{Dict{String,Number},Symbol}}() # rid => (reaction stoichiometry, :forward, :backward, :bidirectional)
annotation_show_text = false
annotation_text_color = :black
annotation_text_size = 12
```

Get or create maps here: `https://escher.github.io/#/`.
