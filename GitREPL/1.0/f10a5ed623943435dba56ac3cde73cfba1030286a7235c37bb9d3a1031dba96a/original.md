```
gitrepl()
gitrepl(; kwargs...)
```

Set up the Git REPL mode.

## Optional keyword arguments

| Name          | Type             | Default Value                |
|:------------- |:---------------- |:---------------------------- |
| `mode_name`   | `AbstractString` | `"GitREPL.jl Git REPL mode"` |
| `prompt_text` | `AbstractString` | `"git> "`                    |
| `start_key`   | `AbstractChar`   | `','`                        |

## Descriptions of optional keyword arguments:

| Name          | Description                                         |
|:------------- |:--------------------------------------------------- |
| `mode_name`   | Name of the REPL mode                               |
| `prompt_text` | Prompt text to display when the REPL mode is active |
| `start_key`   | Key to press to enter the REPL mode                 |
