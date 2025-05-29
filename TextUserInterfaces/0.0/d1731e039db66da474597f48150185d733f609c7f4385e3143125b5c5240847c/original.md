function create_menu(names::Vector{T1}, descriptions::Union{Nothing,Vector{T2}} = nothing; kwargs...)

Create a menu with the names `names` and descriptions `descriptions`. If `descriptions` is `nothing` or is omitted, then the menu descriptions will not be shown.

# Keywords

  * `format`: If `nothing`, then the default menu format will be used. Otherwise,           it must be a tuple with two integers describing respectively the           number of rows and columns. (**Default** = `nothing`)
  * `mark`: The menu mark. (**Default** = `-`)
  * `one_value`: If `true`, then the menu cannot have multiple selections.              (**Default** = `true`)
  * `show_desc`: If `true`, then the menu description will be shown.              (**Default** = `true`)
  * `row_major`: If `true`, then the menu will be constructed in a row-major              ordering.
  * `ignore_case`: If `true`, then the case will be ignored on pattern matching.
  * `show_match`: If `true`, then the cursor will be moved to within the item name               while pattern-matching.
  * `non_cyclic`: If `true`, then the menu will be non cyclic.
