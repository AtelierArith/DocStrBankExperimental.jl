Representation of a lint item.

# Constructors

```julia
LintItem(source, severity::Union{Int, Symbol}, id::Symbol, message::String,
         fixer::Union{Function, Nothing}=nothing, autoapply::Bool=false)
```

`source` is the object that the lint applies to.

`severity` should be one of the following values:

  * `0` or `:debug`, for messages that may assist with debugging problems that may be associated with particular configuration.
  * `1` or `:info`, for informational messages understandable to end-users.
  * `2` or `:warning`, for potentially harmful situations.
  * `3` or `:error`, for severe issues that will prevent normal functioning.

`id` is a symbol representing the type of lint (e.g. `:unknown_driver`)

`message` is a message, intelligible to the end-user, describing the particular nature of the issue with respect to `source`. It should be as specific as possible.

`fixer` can be set to a function which modifies `source` to resolve the issue. If `autoapply` is set to `true` then `fixer` will be called spontaneously. The function should return `true` or `false` to indicate whether it was able to successfully fix the issue.

As a general rule, fixers that do or might require user input should *not* be run automatically, and fixers that can run without any user input and always "do the right thing" should be run automatically.

# Examples

TODO

# Structure

```julia
struct LintItem{S}
    source    ::S
    severity  ::UInt8
    id        ::Symbol
    message   ::String
    fixer     ::Union{Function, Nothing}
    autoapply ::Bool
end
```
