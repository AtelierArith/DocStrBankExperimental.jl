```
to_documenter(p::P; id, version)
```

Take a plot object `p` and returns an output that is showable as HTML inside pages generated from Documenter.jl. This function currently works correctly inside `@example` blocks from Documenter.jl if called as last statement/command. Check the package [documentation](https://disberd.github.io/PlotlyDocumenter.jl) for seeing it in action.

The object returned as output, when shown as `text/html`, will generate a plotly plot can be interacted with directly in the documentation page.

This package supports the following types as `P`:

  * `Plot` from PlotlyBase
  * `SyncPlot` from PlotlyBase
  * `Plot` from PlotlyLight

# Keyword Arguments

  * `id`: The id to be given to the div containing the plot. Defaults to a random string of 10 alphanumeric characters
  * `version`: Version of plotly.js to use. Defaults to version 2.24.2, but can be overridden by providing `version` as a string. To change the default version, use the unexported `change_default_plotly_version` function.
  * `classes`: A Vector of Strings representing classes to assign the div containing the plot. Defaults to an empty vector
  * `style`: An object containing a list of styles that are applied inline to the plot object. Defaults to an empty NTuple. Supports the synthax of [HypertextLiteral](https://juliapluto.github.io/HypertextLiteral.jl/stable/attribute/#Pairs-and-Dictionaries)

# Notes

  * The package does not reexport any plotting packages, so the desired plotting package must be brought in to scope independently.
  * The package currently only supports fetching the plotly library from CDN, so it does not support local version of Plotly (even though they are supported by PlotlyLight for example)
