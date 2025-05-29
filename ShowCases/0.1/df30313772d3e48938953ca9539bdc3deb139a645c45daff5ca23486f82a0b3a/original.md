```
ShowString
```

An `AbstractShow` wrapper for showing strings. This implements some behaviors which are particularly useful for strings, in particular, if the string contains multiple lines, block quotes (`"""`) will be used and indents will be inserted.

## Constructors

  * `ShowString(o; block::Symbol=:context, indent="")`

## Arguments

  * `o`: the object to be wrapped.  Typically, but not necessarily a string.
  * `block::Symbol`: (*options:* `:context`, `:always`, `:never`) whether to print the string as a block.  If `:context`, this   will be done iff the string contains multiple lines.
  * `indent::AbstractString`: indent to use on new lines.
