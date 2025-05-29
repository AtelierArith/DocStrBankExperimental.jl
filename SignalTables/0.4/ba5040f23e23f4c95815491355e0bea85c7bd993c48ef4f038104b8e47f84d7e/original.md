```
signal = Map(; kwargs...)::OrderedDict{Symbol,Any}
```

Returns a set of key/value pairs in form of a dictionary. A Map is used to associate a set of attributes to a Variable, Parameter or Signal Table.

The following keys are recognized (all are *optional*):

| key     | value              |
|:------- |:------------------ |
| `:info` | Short description. |

Additionally, any other signal attributes can be stored in `signal` with a desired key,

# Example

```julia
using SignalTables

sigTable = SignalTable(
   J = Par(value = 0.02),
   attributes = Map(author = "xyz")
)
```
