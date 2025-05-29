```
ShowEntry
```

An `AbstractShow` wrapper type for showing entries in a list.  Allows for specification of list-context options.

## Constructors

  * `ShowEntry(o; new_line=false, indent="    ", delim=Print(", "))`

## Arguments

  * `o`: the object to be wrapped.
  * `new_line::Bool`: whether to show (or print) the entry on a new line.
  * `indent::AbstractString`: If a new line is created (i.e. with `new_line=true`), the created line   will start with this indent.
  * `delim`: An object that will be shown at the end of an entry, typically a comma.  The object passed will be   shown as is, so for example a `", "` *will* print quotes, use `Print(", ")` to omit quotes.

## Examples

```
julia> ShowEntry(1)  # by default we just get commas
1,


julia> ShowEntry("a", new_line=true, indent="__", delim=Print(": "))

__"a":
```
