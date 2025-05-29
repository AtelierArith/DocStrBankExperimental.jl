```
docopt(doc::AbstractString,
       args=ARGS;
       version=nothing,
       help::Bool=true,
       options_first::Bool=false,
       exit_on_error::Bool=true)
```

Parse command-line arguments according to a help message.

Parsed command-line arguments are retuned as a dictionary of arguments of type `Dict{AbstractString,Any}`; keys are argument names or flag names, and values are argument values passed to the command-line arguments.

See http://docopt.org/ for the description language of help.

# Arguments

  * `doc`: description of your command-line interface.
  * `args=ARGS`: argument vector to be parsed.
  * `version=nothing`: version of your command-line tool (e.g. `v"1.0.2"`).
  * `help=true`: show the help when '-h' or '–help' is passed.
  * `options_first=false`: force options to precede positional arguments.
  * `exit_on_error=true`: print the usage and exit when parsing error happens.
