```
show_output_when_hidden(x)
```

Wraps the given input `x` inside a custom HTML code created with `HypertextLiteral.@htl` that adds the `always-show-output` attribute to the calling Pluto cell.

This makes sure that the cell output remains visible in the HTML even when the cell is hidden using the [`ExtendedTableOfContents`](@ref) cell hiding feature. This is mostly useful to allow having cells that generate output to be rendered within the notebook as hidden cells.

The provided attribute will make sure (via CSS) that cell will look exactly like a hidden cell except for its output element. When the output is floating (like for [`BondTable`](@ref) or [`ExtendedTableOfContents`](@ref)), this will make the cell hidden while the rendered output visible.

# Example usage

```julia
BondTable([bonds...]) |> show_output_when_hidden
```

The code above will allow putting the cell defining the `BondTable` within a hidden part of the notebook while still rendering the floating BondTable. Without this function, the `BondTable` generating cell would need to be located inside a non-hidden part of the notebook.

# Note

When calling this function with an input object that is not of type `HTML` or `HypertextLiteral.Result`, the function will wrap the object first using `@htl` and `PlutoRunner.embed_display`. Since the `embed_display` function is only available inside of Pluto,  
