```
AnsiTextCell(string::AbstractString)
```

Create an [`AnsiTextCell`](@ref) using `string`.

```
AnsiTextCell(renderfn[; context])
```

Create an [`AnsiTextCell`](@ref) using a render function.

`renderfn` is a function with the following signature:

```
renderfn(io)::String
```

that renders a string that can contain ANSI sequences into `io`.

`context` is a tuple of context arguments passed to an `IOContext` that `renderfn` receives. See `IOContext` for details on what arguments are available.

Useful for supporting packages that have rich terminal outputs.

## Examples

Below are examples for wrappers around `AnsiTextCell` to print rich data into tables that make use of packages with rich terminal output.

### Crayons.jl

Apply custom decoration to text inside a cell.

```julia
using Crayons, PrettyTables

b = crayon"blue bold"
y = crayon"yellow bold"
g = crayon"green bold"

pretty_table([AnsiTextCell("$(g)This $(y)is $(b)awesome!") for _ in 1:5, _ in 1:5])
```

### ImageInTerminal.jl

Show images inside a table.

```julia
using ImageInTerminal, PrettyTables

function ImageCell(img, size)
    return AnsiTextCell(
        io -> ImageInTerminal.imshow(io, img),
        context = (:displaysize => size,),)
end

using TestImages
img = testimage("lighthouse")
pretty_table([ImageCell(img, (20, 20)) ImageCell(img, (40, 40))])
```

### UnicodePlots.jl

Show a variety of plots in a table.

```julia
using UnicodePlots, PrettyTables

function UnicodePlotCell(p)
    return AnsiTextCell(
        io -> show(io, p),
        context = (:color => true,)
    )
end

pretty_table([
    UnicodePlotCell(barplot(Dict("x" => 10, "y" => 20)))
    UnicodePlotCell(boxplot([1, 3, 3, 4, 6, 10]))
])
```

### CommonMark.jl

Use rich Markdown inside tables.

```julia
using CommonMark, PrettyTables

function MarkdownCell(md)
    return AnsiTextCell(
        renderfn = io -> display(TextDisplay(io), md),
        context = (:color => true,)
    )
end

pretty_table([MarkdownCell(cm"**Hi**") MarkdownCell(cm"> quote")])
```
