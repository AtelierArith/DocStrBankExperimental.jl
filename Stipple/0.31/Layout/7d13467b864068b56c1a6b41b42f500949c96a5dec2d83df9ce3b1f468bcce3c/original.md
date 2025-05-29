```
function theme() :: String
```

Provides theming support for Stipple apps and pages. It includes Stipple's default CSS files and additional elements,   in the form of HTML tags, can be injected by pushing to the `Stipple.Layout.THEMES[][]` collection.

### Example

```julia
julia> theme()
"<link href="https://fonts.googleapis.com/css?family=Material+Icons" rel="stylesheet" /><link href="https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;0,900;1,400&display=swap" rel="stylesheet" /><link href="/css/stipple/stipplecore.css" rel="stylesheet" />"

julia> StippleUI.theme()
"<link href="/css/stipple/quasar.min.css" rel="stylesheet" />"

julia> push!(Stipple.Layout.THEMES[], StippleUI.theme)
```
