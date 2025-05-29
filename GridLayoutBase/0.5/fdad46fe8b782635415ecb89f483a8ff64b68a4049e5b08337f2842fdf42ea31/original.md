```
mutable struct LayoutObservables{T, G}
```

`T` is the same type parameter of contained `GridContent`, `G` is `GridLayout` which is defined only after `LayoutObservables`.

A collection of `Observable`s and an optional `GridContent` that are needed to interface with the MakieLayout layouting system.

  * `suggestedbbox::Observable{FRect2D}`: The bounding box that an element should place itself in. Depending on the element's `width` and `height` attributes, this is not necessarily equal to the computedbbox.
  * `protrusions::Observable{RectSides{Float32}}`: The sizes of content "sticking out" of the main element into the `GridLayout` gaps.
  * `reportedsize::Observable{NTuple{2, Optional{Float32}}}`: The width and height that the element computes for itself if possible (else `nothing`).
  * `autosize::Observable{NTuple{2, Optional{Float32}}}`: The width and height that the element reports to its parent `GridLayout`. If the element doesn't want to cause the parent to adjust to its size, autosize can hide the reportedsize from it by being set to `nothing`.
  * `computedbbox::Observable{FRect2D}`: The bounding box that the element computes for itself after it has received a suggestedbbox.
  * `gridcontent::Optional{GridContent{G, T}}`: A reference of a `GridContent` if the element is currently placed in a `GridLayout`. This can be used to retrieve the parent layout, remove the element from it or change its position, and assign it to a different layout.
