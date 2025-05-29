```
create_canvas(
            id::Union{Int,String};
            ncol::Int = 1,
            nrow::Int = 1,
            axids::Array{Int,1} = Int[],
            figsize::Tuple{Number,Number} = (0.5+ncol*3, 0.5+nrow*3),
            dpi::Number = 100
)
```

Create a canvas, given

  * `id` ID of the figure
  * `ncol` Number of columns in the figure
  * `nrow` Number of rows in the figure
  * `axids` Given indicies of the subplots in the figure
  * `figsize` Given canvas size
  * `dpi` Given pixels per inch
