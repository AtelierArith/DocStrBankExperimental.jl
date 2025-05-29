```
function drawplasmid(chr; kwargs...)
```

Draw a circular plasmid map. CDSs are displayed as boxes on the outside and inside of the plasmid, for genes on the + and - strands, respectively. Supported kwargs are:

  * outfile           Path to output file. Supported file types are PNG, SVG, PDF, and EPS.
  * drawingsize       Size of the figure, can be a `Tuple{Int,Int}`, or a `String` such as "1000x1000".
  * title             Name of the plasmid.
  * ORI               The position of the ORI (defaults to 1).
  * colors            A `Dict`, with `Gene`s as keys and colors as values (defaults to `defaultgenecolor`).
  * defaultgenecolor  Defaults to :lightgrey.
  * annotations       A `Vector` containing annotations for each CDS.
  * internalcolors    A `Dict` with `UnitRange`s (representing nucleotide positions) as keys, and colors as values. Can be used to color parts of genes, or intergenic regions.
  * genethickness     Size of the gene boxes.
  * textoffset        Distance from the plasmid where annotations should be drawn.
  * figureoffset      A `Tuple{Int,Int}` with offsets in the x and y axes, respectively. Useful if there are more annotations on one side than the other.
  * genegroups        A `Dict` with `UnitRanges` as keys (representing gene numbers), and `NamedTuples` as values. The tuple must have the field `text`, which contains the annotations for the group, and can additionally take `placement` (:outer or :inner), `offset`, `textoffset`, and `thickness`.
