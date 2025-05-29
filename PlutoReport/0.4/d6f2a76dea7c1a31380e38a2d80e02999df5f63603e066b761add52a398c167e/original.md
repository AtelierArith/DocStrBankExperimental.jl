```
presentation_controls(aside::Bool = true) :: PlutoUI.CombineNotebook.CombinedBonds
```

Returns a PlutoUI widget which returns a [`PresentationControls`](@ref), and acts as a control panel for [`presentation_ui`](@ref). Must be bound to a variable using `PlutoUI.bind`.

# Arguments

  * `aside::Bool`: Whether control panel is floating

See also [`presentation_ui`](@ref), [`PresentationControls`](@ref)
