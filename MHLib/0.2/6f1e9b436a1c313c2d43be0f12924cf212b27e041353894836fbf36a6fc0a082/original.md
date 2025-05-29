```
settings::Dict{Symbol, Any}
```

Global settings, i.e., dictionary with all parameters and their values.

Settings can be given by command line arguments, in a configuration file, or in code, e.g., provided in the main program.

For using application-specific settings, define them via `ArgParseSettings` and  `@add_arg_table!`nand call `parse_settings!`, values can then be accessed  via `settings[:<name>]::<Type>`. The type-cast is optional but may frequently help to achieve type-stability.
