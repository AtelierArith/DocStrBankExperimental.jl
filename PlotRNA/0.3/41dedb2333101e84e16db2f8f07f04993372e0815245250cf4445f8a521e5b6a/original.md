```
plot_structure(structure; [sequence, savepath, more plot opts...]) -> Luxor.Drawing
```

Plot an RNA secondary structure given by `structure` and optionally `sequence`. If `savepath` is nonempty the image is written there.

Plot options:

  * `layout_type=:simple` graph layout algorithm, one of `:simple`, `:naview`, `:circular`, `:turtle`, `:puzzler`
  * `base_colors=Float64[]` base color to choose from `base_colorscheme`, vector of values 0.0 to 1.0
  * `base_colorscheme::ColorScheme=colorschemes[:flag_id]`
