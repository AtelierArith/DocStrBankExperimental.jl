```
NonDisRES <: AbstractNonDisRES
```

A non-dispatchable renewable energy source. It extends the existing `RefSource` node through including a profile that corresponds to the production. The profile can have variations on the strategic level.

# Fields

  * **`id`** is the name/identifyer of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`profile::TimeProfile`** is the power production in each operational period as a ratio of the installed capacity at that time.
  * **`opex_var::TimeProfile`** is the variable operating expense per energy unit produced.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense.
  * **`output::Dict{Resource, Real}`** are the generated `Resource`s, normally Power.
  * **`data::Vector{Data}`** is the additional data (e.g. for investments). The field `data` is conditional through usage of a constructor.
