```
Command(name, parameters, arguments, subcommands)
```

Represent a command to be executed, with associated flags, options, arguments, and subcommands.

# Arguments

  * `name::String`: the name of the command.
  * `parameters`: an iterable of flags and options.
  * `arguments::Vector{String}`: any arguments to the command.
  * `subcommands::Vector{AbstractCommand}`: any subcommands to be executed in conjunction with the main command.
