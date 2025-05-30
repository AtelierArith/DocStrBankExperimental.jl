A group of checkboxes (`<input type="checkbox">`) - the user can choose enable or disable of the `options`, an array of `Strings`. The value returned via `@bind` is a list containing the currently checked items.

See also: [`MultiSelect`](@ref).

`options` can also be an array of pairs `key::String => value::Any`. The `key` is returned via `@bind`; the `value` is shown.

`defaults` specifies which options should be checked initally.

`orientation` specifies whether the options should be arranged in `:row`'s `:column`'s.

`select_all` specifies whether or not to include a "Select All" checkbox.

# Examples

`@bind snacks MultiCheckBox(["🥕", "🐟", "🍌"]))`

`@bind snacks MultiCheckBox(["🥕" => "🐰", "🐟" => "🐱", "🍌" => "🐵"]; default=["🥕", "🍌"])`

`@bind animals MultiCheckBox(["🐰", "🐱" , "🐵", "🐘", "🦝", "🐿️" , "🐝",  "🐪"]; orientation=:column, select_all=true)`
