```
replay(instructions::Vector{<:AbstractString}, buf::IO; kwargs...)
```

Replay the REPL output from given instructions.

## Keyword Arguments

### Replay options

  * `use_ghostwriter`: Flag to enable ghostwriter mode. (default: `true`)

### Julia options

  * `julia_project`: Path to a project where julia process runs. (default: `@.`)
  * `cmd`: Additional command for julia process. (default: `"--color=yes"`)
