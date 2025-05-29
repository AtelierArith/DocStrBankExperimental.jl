```
prompt_char(question::AbstractString, options::Vector{Char},
            default::Union{Char, Nothing}=nothing)
```

Interactively ask `question`, only accepting `options` keys as answers. All keys are converted to lower case on input. If `default` is not nothing and 'RET' is hit, then `default` will be returned.

Should '^C' be pressed, an InterruptException will be thrown.
