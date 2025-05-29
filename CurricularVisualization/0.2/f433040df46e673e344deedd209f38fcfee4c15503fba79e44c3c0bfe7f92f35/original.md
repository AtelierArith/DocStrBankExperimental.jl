```
homology(curricula; <keyword arguments>)
```

Given a collection of `Curriculum` data objects as input, provide a visulaization that shows how similar each  curriculum is (in terms of shared courses) to every other curriculum in the collection.  With the default color scheme, lighter colors indicate hihger similarity, with the color on the main diagonal (the similarity of a curriculum to itself) indicating maximal similarity.

# Arguments

Required:

  * `curricula::Array{Curriculum,1}` : the collection of curricula that will be analzyed for similarity.

Keyword:

  * `strict::Bool` : if true, strictly match courses (including course ID); if false (default), match only course name or courese prefix and number.
  * `title::AbstractString` : the title that will appear above the visualization, default is the empty string.
  * `xlabel::AbstractString` : the label below the x-axis, default is the empty string.
  * `ylabel::AbstractString` : the label below the x-axis, default is the empty string.
  * `color::Symbol` : the color gradient used to plot similarity values, default is the symbol `:thermal`.  Other color schemes symbols
  * `legend::Bool` : display a plot legend, default is `false`.

To see the color libraries avaiable to you, type:

```julia-repl
julia> clibraries()
```

Then pick one of these color libraries, and use the following function to see the color scheme symbols available in that library, e.g.,

```julia-repl
julia> showlibrary(:cmocean)
```
