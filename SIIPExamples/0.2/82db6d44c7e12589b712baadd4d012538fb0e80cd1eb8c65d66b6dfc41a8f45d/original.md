`notebook(example::Type{<:Examples}; kwargs...)`

Launches a notebook server for the specified `Examples` folder.

# Arguments

  * `example::Type{<:Examples}`: The example category `JuliaExamples`, `PSYExamples`, `PSIExamples`, or `PSDExamples`
  * `notebook_target_dir = mktempdir()`: directory to create notebooks and launch server

# Example

`notebook(PSYExamples,  ".")`
