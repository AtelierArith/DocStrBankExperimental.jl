```
(maker::ToggleMenuMaker)(options[, selections])::ToggleMenu
(maker::ToggleMenuMaker)(opts::Tuple{StringVector,Vector{Char}})::ToggleMenu
(maker::ToggleMenuMaker)(header::AbstractString, options...)::ToggleMenu
```

Make a `ToggleMenu`.

The `options` are a Vector of some String type, which have states which may be toggled through. `selections` is an optional `Vector{Char}` of initial selected states for the options.  If a selection is `\0`, the menu will skip that line during navigation, and it will not be togglable.  If not provided, the menu options will begin in the first setting.

If you want a header specific to one menu, provide it as the first argument, this will override the header in the `maker` (which can be "" if desired).

When the menu is finished, it will return a `Vector` of `Tuples`, the first of which is a selection, the last an option.  This precomposes the options with their selections, which is probably what you want, as well as allowing menu functions to modify both options and selections.  If canceled, all selections will be `\0`.

# Use

[`ToggleMenu`](@ref)s are inherently designed for use at the [`REPL`](@extref `stdlib/REPL`), and the type signatures are designed for easy composition.  For example, this works:

```julia
julia> (["option 1", "option 2"], ['a', 'b']) |> maker |> request
```

Which is more useful with a function which prepares options and selections. Once that function is stable one may use composition:

```julia
action = request ∘ maker ∘ prepare
```

Such that `action(data)` will prepare data to be presented in ToggleMenu format, pass it to the `maker`, and call `request`.

`ToggleMenus` also adds methods to `request` to make `do` notation possible for `ToggleMenus`, making this sort of workflow possible:

```julia
request(menu(options, selections)) do selected
    # handle the returned settings here
end
```
