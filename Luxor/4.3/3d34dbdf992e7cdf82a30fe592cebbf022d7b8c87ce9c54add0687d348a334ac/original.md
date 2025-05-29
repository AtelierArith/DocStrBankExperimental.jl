```
setmode(mode::AbstractString)
```

Set the compositing/blending mode. `mode` can be one of:

  * `"clear"` Where the second object is drawn, the first is completely removed.
  * `"source"` The second object is drawn as if nothing else were below.
  * `"over"` The default mode: like two transparent slides overlapping.
  * `"in"` The first object is removed completely, the second is only drawn where the first was.
  * `"out"` The second object is drawn only where the first one wasn't.
  * `"atop"` The first object is mostly intact, but mixes both objects in the overlapping area. The second object is not drawn elsewhere.
  * `"dest"` Discard the second object completely.
  * `"dest_over"` Like "over" but draw second object below the first
  * `"dest_in"` Keep the first object whereever the second one overlaps.
  * `"dest_out"` The second object is used to reduce the visibility of the first where they overlap.
  * `"dest_atop"` Like "over" but draw second object below the first.
  * `"xor"` XOR where the objects overlap
  * `"add"` Add the overlapping areas together
  * `"saturate"` Increase Saturation where objects overlap
  * `"multiply"` Multiply where objects overlap
  * `"screen"` Input colors are complemented and multiplied, the product is complemented again. The result is at least as light as the lighter of the input colors.
  * `"overlay"` Multiplies or screens colors, depending on the lightness of the destination color.
  * `"darken"` Selects the darker of the color values in each component.
  * `"lighten"` Selects the lighter of the color values in each component.

See the [Cairo documentation](https://www.cairographics.org/operators/) for details.
