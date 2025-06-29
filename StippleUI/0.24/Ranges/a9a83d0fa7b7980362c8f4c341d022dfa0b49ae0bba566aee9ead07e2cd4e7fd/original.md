```
range(range::AbstractRange{<:Union{Symbol, String, Real}}, fieldname::Union{Symbol,Nothing} = nothing, args...; lazy = false, kwargs...)
```

The `range` component is a great way to offer the user the selection of a sub-range of values between a minimum and maximum value, with optional steps to select those values. An example use case for the Range component would be to offer a price range selection

---

### Examples

---

### Model

```julia-repl
julia> @vars RangeModel begin
         range_data::R{RangeData{Int}} = RangeData(18:80)
       end
```

### View

```julia-repl
julia> range(18:1:90,
          :range_data;
          label=true,
          color="purple",
          labelalways=true,
          labelvalueleft=Symbol("'Min age: ' + range_data.min"),
          labelvalueright=Symbol("'Max age: ' + range_data.max")
       )
```

---

### Arguments

---

1. Behaviour

      * `name::String` - Used to specify the name of the control; Useful if dealing with forms submitted directly to a URL ex. `car_id`
      * `snap::Bool` - Snap on valid values, rather than sliding freely; Suggestion: use with 'step' property
      * `reverse::Bool` - Work in reverse (changes direction)
      * `vertical::Bool` - Display in vertical direction
      * `labelalways::Bool` - Always display the label
2. Content

      * `label::Bool` - Popup a label when user clicks/taps on the slider thumb and moves it
      * `markers::Union{Bool, Int}` - Display markers on the track, one for each possible value for the model or using a custom step (when specifying a Number) ex. `markers` `markers="5"`
      * `dragrange::Bool` - User can drag range instead of just the two thumbs
      * `dragonlyrange::Bool` - User can drag only the range instead and NOT the two thumbs
3. General

      * `tabindex::Union{Int, String}` - Tabindex HTML attribute value ex. `0` `100`
4. Labels

      * `labelcolorleft::String` - Color name for left label background from the [Color Palette](https://quasar.dev/style/color-palette) ex. `primary` `teal-10`
      * `labeltextcolorleft::String` - Color name for left label text from the [Color Palette](https://quasar.dev/style/color-palette) ex. `primary` `teal-10`
      * `labelcolorright::String` - Color name for right label background from the [Color Palette](https://quasar.dev/style/color-palette) ex. `primary` `teal-10`
      * `labeltextcolorright::String` - Color name for right label text from the [Color Palette](https://quasar.dev/style/color-palette) ex. `primary` `teal-10`
      * `labelvalueleft::Union{String, Int}` - Override default label for min value ex. `labelvalueleft="model.min + 'px'"`
      * `labelvalueright::Union{String, Int}` - Override default label for max value ex. `labelvalueright="model.max + 'px'"`
5. Model

      * `range::AbstractRange{T}` - The range of values to select from min:step:max, symbols or strings can be used to reference model fields, e.g. `range("min":2:"max", :myvalue)`
      * `lazy::Bool` - If true, update the value of the model field only upon release of the slider
6. State

      * `disable::Bool` - Put component in disabled mode
      * `readonly::Bool` - Put component in readonly mode
7. Style

      * `color::String` - Color name for component from the [Color Palette](https://quasar.dev/style/color-palette) ex. `primary` `teal-10`
      * `labelcolor::String` - Color name for component from the [Color Palette](https://quasar.dev/style/color-palette) ex. `primary` `teal-10`
      * `thumbpath::String` - Set custom thumb svg path ex. `M5 5 h10 v10 h-10 v-10`
      * `dark::Bool` - Notify the component that the background is a dark color
      * `dense::Bool` - Dense mode; occupies less space
