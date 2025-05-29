```
confirm_yn(question::AbstractString, default::Bool=false)
```

Interactively ask `question` and accept y/Y/n/N as the response. If any other key is pressed, then `default` will be taken as the response. A " [y/n]: " string will be appended to the question, with y/n capitalised to indicate the default value.

### Example

```julia-repl
julia> confirm_yn("Do you like chocolate?", true)
Do you like chocolate? [Y/n]: y
true
```
