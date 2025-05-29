A command that can be used in the Data REPL (accessible through '}').

A `ReplCmd` must have a:

  * `name`, a symbol designating the command keyword.
  * `trigger`, a string used as the command trigger (defaults to `String(name)`).
  * `description`, a short overview of the functionality as a `string` or `display`able object.
  * `execute`, either a list of sub-ReplCmds, or a function which will perform the command's action. The function must take a single argument, the rest of the command as an `AbstractString` (for example, 'cmd arg1 arg2' will call the execute function with "arg1 arg2").

# Constructors

```julia
ReplCmd{name::Symbol}(trigger::String, description::Any, execute::Function)
ReplCmd{name::Symbol}(description::Any, execute::Function)
ReplCmd(name::Union{Symbol, String}, trigger::String, description::Any, execute::Function)
ReplCmd(name::Union{Symbol, String}, description::Any, execute::Function)
```

# Examples

```julia
ReplCmd(:echo, "print the argument", identity)
ReplCmd(:addone, "return the input plus one", v -> 1 + parse(Int, v))
ReplCmd(:math, "A collection of basic integer arithmetic",
    [ReplCmd(:add, "a + b + ...", nums -> sum(parse.(Int, split(nums))))],
     ReplCmd(:mul, "a * b * ...", nums -> prod(parse.(Int, split(nums)))))
```

# Methods

```julia
help(::ReplCmd) # -> print detailed help
allcompletions(::ReplCmd) # -> list all candidates
completions(::ReplCmd, sofar::AbstractString) # -> list relevant candidates
```
