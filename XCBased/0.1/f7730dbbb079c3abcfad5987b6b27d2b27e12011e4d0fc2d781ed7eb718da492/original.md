```
XCBVisualType
```

Visual information allowed for some depth(s) of some screen(s). See [`XCBScreen`](@ref). The struct has the following fields:

  * `visual_id` – the XID corresponding to the visual type
  * `class` – one of `XCB_VISUAL_CLASS_STATIC_GRAY`, `XCB_VISUAL_CLASS_GRAY_SCALE`, `XCB_VISUAL_CLASS_STATIC_COLOR`, `XCB_VISUAL_CLASS_PSEUDO_COLOR`, `XCB_VISUAL_CLASS_TRUE_COLOR`, and `XCB_VISUAL_CLASS_DIRECT_COLOR`
  * `bits_per_rgb_value` – the log2 of the number of distinct color intensity values (individually) of red, green, and blue
  * `colormap_entries` – the number of available colormap entries in a newly created colormap
  * `red_mask` – only defined for `XCB_VISUAL_CLASS_DIRECT_COLOR` and `XCB_VISUAL_CLASS_TRUE_COLOR`
  * `green_mask` – only defined for `XCB_VISUAL_CLASS_DIRECT_COLOR` and `XCB_VISUAL_CLASS_TRUE_COLOR`
  * `blue_mask` – only defined for `XCB_VISUAL_CLASS_DIRECT_COLOR` and `XCB_VISUAL_CLASS_TRUE_COLOR`
