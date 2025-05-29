```
datefield(args...; kwargs...)
```

Complex input type that combines a textfield with an icon, a datepicker and a popup. The datepicker is hidden by default and is shown when the icon is clicked. The popup is used to hide the datepicker when the user clicks outside of it. A number of common arguments are defined and are passed to the textfield, the icon, the popup and the datepicker. In addition, keyword arguments can be passed to each of these components individually by using the `textfield_props`, `icon_props`, `popup_proxy_props` and `datepicker_props` keyword arguments.

### Examples

```julia
datefield("Start date", :start_date, datepicker_props = Dict(:todaybtn => true, :nounset => true), textfield_props = Dict(:bgcolor => "green-1"))
```
