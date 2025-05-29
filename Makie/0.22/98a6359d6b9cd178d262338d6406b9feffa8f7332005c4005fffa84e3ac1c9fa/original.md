```
crossbar(x, y, ymin, ymax; kwargs...)
```

Draw a crossbar. A crossbar represents a range with a (potentially notched) box. It is most commonly used as part of the `boxplot`.

## Arguments

  * `x`: position of the box
  * `y`: position of the midline within the box
  * `ymin`: lower limit of the box
  * `ymax`: upper limit of the box

## Plot type

The plot type alias for the `crossbar` function is `CrossBar`.

## Attributes

**`color`** =  `@inherit patchcolor`  — *No docs available.*

**`colormap`** =  `@inherit colormap`  — *No docs available.*

**`colorrange`** =  `automatic`  — *No docs available.*

**`colorscale`** =  `identity`  — *No docs available.*

**`cycle`** =  `[:color => :patchcolor]`  — *No docs available.*

**`dodge`** =  `automatic`  — *No docs available.*

**`dodge_gap`** =  `0.03`  — *No docs available.*

**`gap`** =  `0.2`  — Shrinking factor, `width -> width * (1 - gap)`.

**`inspectable`** =  `@inherit inspectable`  — *No docs available.*

**`midlinecolor`** =  `automatic`  — *No docs available.*

**`midlinewidth`** =  `@inherit linewidth`  — *No docs available.*

**`n_dodge`** =  `automatic`  — *No docs available.*

**`notchmax`** =  `automatic`  — Upper limit of the notch.

**`notchmin`** =  `automatic`  — Lower limit of the notch.

**`notchwidth`** =  `0.5`  — Multiplier of `width` for narrowest width of notch.

**`orientation`** =  `:vertical`  — Orientation of box (`:vertical` or `:horizontal`).

**`show_midline`** =  `true`  — Show midline.

**`show_notch`** =  `false`  — Whether to draw the notch.

**`strokecolor`** =  `@inherit patchstrokecolor`  — *No docs available.*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *No docs available.*

**`width`** =  `automatic`  — Width of the box before shrinking.
