```julia
@datax
```

Print the arguments to a data file to be read by pgfkeys. Best used with the [`datax` LaTeX package](https://ctan.org/pkg/datax). Variables can be supplied either by name or as assignments, and meta-arguments are supplied using the `:=` operator.

The meta-arguments include all the keyword arguments from `Latexify.jl` and `UnitfulLatexify.jl` (for instance `unitformat := :siunitx`, `fmt := "%.2e"`), as well as a few extra:

# Meta-arguments

  * `filename`: The path to a file that will be written.
  * `io`: an `IO` object to write to instead of a file. Overrides the `filename` argument. If neither this nor `filename` is given, `stdout` is used.
  * `permissions`: Defaults to `"w"`. Can be given as `"a"` to append to a file instead of overwriting. Only meaningful with a `filename` argument.

# Examples

```julia
julia> a = 2;
julia> b = 3.2u"m";
julia> @datax a b c=3*a d=27 unitformat:=:siunitx
\pgfkeyssetvalue{/datax/a}{\num{2}}
\pgfkeyssetvalue{/datax/b}{\qty{3.2}{\meter}}
\pgfkeyssetvalue{/datax/c}{\num{6}}
\pgfkeyssetvalue{/datax/d}{\num{27}}

```
