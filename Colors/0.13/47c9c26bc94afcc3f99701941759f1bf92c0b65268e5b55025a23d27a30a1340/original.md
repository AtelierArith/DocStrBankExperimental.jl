```
colors = distinguishable_colors(n, seed=RGB{N0f8}[];
                                dropseed=false,
                                transform=identity,
                                lchoices=range(0, stop=100, length=15),
                                cchoices=range(0, stop=100, length=15),
                                hchoices=range(0, stop=342, length=20))
```

Generate `n` maximally distinguishable colors.

This uses a greedy brute-force approach to choose `n` colors that are maximally distinguishable. Given seed color(s), and a set of possible hue, chroma, and lightness values (in LCHab space), it repeatedly chooses the next color as the one that maximizes the minimum pairwise distance to any of the colors already in the palette.

# Arguments

  * `n`: Number of colors to generate.
  * `seed`: Initial color(s) included in the palette.

# Keyword arguments

  * `dropseed`: if true, the `seed` values will be dropped. This provides an easy mechanism to ensure that the chosen colors are distinguishable from the seed value(s). When true, `n` does not include the seed color(s).
  * `transform`: Transform applied to colors before measuring distance. Default is `identity`; other choices include `deuteranopic` to simulate color-blindness.
  * `lchoices`: Possible lightness values
  * `cchoices`: Possible chroma values
  * `hchoices`: Possible hue values

Returns a `Vector` of colors of length `n`, of the type specified in `seed`.
