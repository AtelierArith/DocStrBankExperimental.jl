```
escape_value(value::AbstractString)::String
```

Given some raw `value` (name of an axis, axis entry or property, or a parameter value), which may contain special characters, return an escaped version to be used as a single value [`Token`](@ref).

We need to consider the following kinds of characters:

  * **Safe** ([`is_value_char`](@ref)) characters include `a` - `z`, `A` - `Z`, `0` - `9`, `_`, `+`, `-`, and `.`, as well as any non-ASCII (that is, Unicode) characters. Any sequence of these characters will be considered a single value [`Token`](@ref). These cover all the common cases (including signed integer and floating point values).
  * All other ASCII characters are (at least potentially) **special**, that is, may be used to describe an operation.
  * Prefixing **any** character with a `\` allows using it inside a value [`Token`](@ref). This is useful if some name or value contains a special character. For example, if you have a cell whose name is `ACTG:Plate1`, and you want to access the name of the batch of this specific cell, you will have to write `/ cell = ACTG\:Plate1 : batch`.

!!! note
    The `\` character is also used by Julia inside `"..."` string literals, to escape writing non-printable characters. For example, `"\n"` is a single-character string containing a line break, and therefore `"\\"` is used to write a single `\`. Thus the above example would have to be written as `"cell = ACTG\\:Plate1 : batch"`. This isn't nice.

    Luckily, Julia also has `raw"..."` string literals that work similarly to Python's `r"..."` strings (in Julia, `r"..."` is a regular expression, not a string). Inside raw string literals, a `\` is a `\` (unless it precedes a `"`). Therefore the above example could also be written as `raw"/ cell = ACTG\:Plate1 : batch`, which is more readable.


Back to `escape_value` - it will prefix any special character with a `\`. It is useful if you want to programmatically inject a value. Often this happens when using `$(...)` to embed values into a query string, e.g., do not write a query `/ $(axis) @ $(property)` as it is unsafe, as any of the embedded variables may contain unsafe characters. You should instead write something like `/ $(escape_value(axis)) @ $(escape_value(property))`.
