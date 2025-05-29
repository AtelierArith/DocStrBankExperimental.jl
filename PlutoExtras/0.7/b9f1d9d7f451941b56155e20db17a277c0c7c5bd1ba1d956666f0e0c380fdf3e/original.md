```
Editable(x::Real; [prefix, suffix, format])
```

Create a Pluto widget similar to [`Scrubbable`](@ref) from PlutoUI but that can contain an arbitrary (Real) number provided as input.

The displayed HTML will create a span with a blue background which contains the number and is preceded by an optional text `prefix` and an optional text `suffix`. If `format` is specified, it will be used to format the shown number using the [d3-format](https://github.com/d3/d3-format#locale_format) specification.

The widget will trigger a bond update only upon pressing Enter or moving the focus out of the widget itself.

![79f77981-2c53-4ff0-bd13-8213519e0bca](https://github.com/disberd/PlutoExtras.jl/assets/12846528/cb0f19e3-7dcb-46d6-88b1-1bbe1592dd1c)

# Keyword Arguments

  * `prefix::AbstractString`: A string that will be inserted in the displayed HTML before the number. Clicking on the suffix will select the full text defining the number
  * `suffix::AbstractString`: A string that will be inserted in the displayed HTML after the number. Clicking on the suffix will select the full text defining the number
  * `format::AbstractString`: A string specifing the format to use for displaying the number in HTML. Uses the [d3-format](https://github.com/d3/d3-format#locale_format) specification
