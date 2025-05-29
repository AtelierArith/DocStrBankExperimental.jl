```
@typeparams typedef
```

Automatically generate type parameters for fields of the form `fieldname::{...}`.

# Examples

```
julia> @macroexpand(
       @typeparams struct T
           a::{}
       end)
:(struct T{var"##a#1"}
      a::var"##a#1"
  end)

julia> @macroexpand(
       @typeparams struct T
           a::{<:Integer}
       end)
:(struct T{var"##a#1" <: Integer}
      a::var"##a#1"
  end)

julia> @macroexpand(
       @typeparams struct T
            a::{A}
       end)
:(struct T{A}
      a::A
  end)
```
