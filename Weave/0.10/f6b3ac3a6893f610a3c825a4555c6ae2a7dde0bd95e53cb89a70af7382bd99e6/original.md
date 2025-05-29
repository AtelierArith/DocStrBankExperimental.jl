```
notebook(source::AbstractString; kwargs...)
```

Convert Weave document `source` to Jupyter Notebook and execute the code using [`nbconvert`](https://nbconvert.readthedocs.io/en/latest/). **Ignores** all chunk options.

## Keyword options

  * `out_path::Union{Symbol,AbstractString} = :pwd`: Path where the output is generated can be either of:

      * `:doc`: Path of the source document
      * `:pwd`: Julia working directory (default)
      * `"somepath"`: `String` of output directory e.g. `"~/outdir"`, or of filename e.g. `"~/outdir/outfile.tex"`
  * `timeout = -1`: nbconvert cell timeout in seconds. Defaults to `-1` (no timeout)
  * `nbconvert_options::AbstractString = ""`: `String` of additional options to pass to nbconvert, such as `"--allow-errors"`
  * `jupyter_path::AbstractString = "jupyter"`: Path/command for the Jupyter you want to use. Defaults to `"jupyter"`, which runs whatever is linked/alias to that

!!! warning
    The code is ***not*** executed by Weave, but by [`nbconvert`](https://nbconvert.readthedocs.io/en/latest/). This means that the output doesn't necessarily always work properly; see [#116](https://github.com/JunoLab/Weave.jl/issues/116).


!!! note
    In order to *just* convert Weave document to Jupyter Notebook, use [`convert_doc`](@ref) instead.

