```
v_unit = unitAsParseableString(v::[Number|AbstractArray])::String
```

Returns the unit of `v` as a string that can be parsed with `Unitful.uparse`.

This allows, for example, to store a quantity with units into a JSON File and recover it when reading the file. This is not (easily) possible with current Unitful functionality, because `string(unit(v))` returns a string that cannot be parse with `uparse`. In Julia this is an unusual behavior because `string(something)` typically returns a string representation of something that can be again parsed by Julia. For more details, see [Unitful issue 412](https://github.com/PainterQubits/Unitful.jl/issues/412).

Most likely, `unitAsParseableString(..)` cannot handle all occuring cases.

# Examples

```julia
using SignalTables
using Unitful

s = 2.1u"m/s"
v = [1.0, 2.0, 3.0]u"m/s"

s_unit = unitAsParseableString(s)  # ::String
v_unit = unitAsParseableString(v)  # ::String

s_unit2 = uparse(s_unit)  # :: Unitful.FreeUnits{(m, s^-1), ..., nothing}
v_unit2 = uparse(v_unit)  # :: Unitful.FreeUnits{(m, s^-1), ..., nothing}

@show s_unit   # = "m*s^-1"
@show v_unit   # = "m*s^-1"

@show s_unit2  # = "m s^-1"
@show v_unit2  # = "m s^-1"
```
