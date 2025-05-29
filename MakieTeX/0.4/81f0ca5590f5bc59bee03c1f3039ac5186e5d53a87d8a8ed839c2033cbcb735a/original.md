```
CachedSVG(svg::SVGDocument)
```

Holds an SVG document along with an Rsvg handle and a Cairo surface to which it has already been rendered.

## Usage

```julia
CachedSVG(read("path/to/svg.svg"))
CachedSVG(read("path/to/svg.svg", String))
CachedSVG(SVGDocument(...))
```

## Fields

  * `doc`: The original `SVGDocument` which is cached here, i.e., the text of that SVG.
  * `handle`: A pointer to the Rsvg handle of the SVG.  May be randomly GC'ed by Rsvg, so is stored as a `Ref` in case it has to be refreshed.
  * `dims`: The dimensions of the SVG in points, for ease of access.
  * `surf`: A Cairo surface to which Rsvg has drawn the SVG.  Permanent and cached.
  * `image_cache`: A cache for a (rendered*image, scale*factor) pair.  This is used to avoid re-rendering the PDF.
