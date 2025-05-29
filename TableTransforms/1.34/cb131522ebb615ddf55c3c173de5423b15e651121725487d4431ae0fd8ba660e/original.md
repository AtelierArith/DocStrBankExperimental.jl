```
Unit(unit)
```

Converts the units of all columns in the table to `unit` from Unitful.jl.

```
Unit(cols₁ => unit₁, cols₂ => unit₂, ..., colsₙ => unitₙ)
```

Converts the units of selected columns `cols₁`, `cols₂`, ..., `colsₙ` to `unit₁`, `unit₂`, ... `unitₙ`.

Unitless columns become unitful if they are explicitly selected.

# Examples

```julia
Unit(u"m")
Unit(1 => u"km", :b => u"K", "c" => u"s")
Unit([2, 3] => u"cm")
Unit([:a, :c] => u"cm")
Unit(["a", "c"] => u"cm")
Unit(r"[abc]" => u"km")
```
