```
@main
@main <function definition>
```

Main entry of the CLI application.

# Quick Example

```julia
# in a script or module

"""
sum two numbers.

# Args

- `x`: first number
- `y`: second number

# Options

- `-p, --precision=<type>`: precision of the calculation.

# Flags

- `-f, --fastmath`: enable fastmath.

"""
@main function sum(x, y; precision::String="float32", fastmath::Bool=false)
    # implementation
    return
end
```

# CLI Definitions and Julia Syntax Mapping

**positional arguments** normal inputs, these are mapped as Julia function arguments, e.g

```shell
sum 1 2
```

`sum` is the command, and `1`, `2` are positional arguments.

**options** arguments with syntax `--<name>=<value>` or `--<name> <value>`, these are mapped as Julia keyword arguments, e.g

```shell
sum --precision=float32 1 2
```

`--precision` is the option of command `sum` and has value `float32`.

**short options** arguments with syntax `-<letter>=<value>` or `-<letter><value>` or `--<letter> <value>`, the letter is usually the first character of a normal option, e.g

```shell
sum -pfloat32 1 2
```

`-p` is the same as `--precision`, but in short hand, this is enabled by writing corresponding docstring (see the next section on docstring syntax).

**flags** like options, but without any value, e.g `--<name>`, this is mapped to a special type of keyword argument that is of type `Bool` and has default value `false`, e.g

```shell
sum --fastmath
```

**short flags** flags with syntax `-<letter>`, the letter should be the first character of the corresponding normal flag, e.g

```shell
sum -f
```

# Doc String Syntax

Each different kind of inputs must have a different level-1 section (markdown syntax `#<section name>`).

The docstring must have section name:

  * `#Args` or `#Arguments` to declare the documentation   of positional arguments.
  * `#Options` to declare the documentation of options.
  * `#Flags` to declare the documentation of flags.

# Examples

The simplest usage is creating the following commands

```julia
"""
an example command

# Args

- `x`: first argument
- `y`: second argument
- `z`: last argument

# Flags

- `-f, --flag`: a flag, optionally can be a short flag.

# Options

- `-o, --option=<int>`: an option, optionally can be short option.

"""
@cast function mycommand(x, y, z; flag::Bool=false, option::Int=2)
    # some implementation
    return
end

@cast function myothercommand(xs...)
    # another command with variatic arguments
    return
end

"""
My main command.
"""
@main # declare the entry
```

this can be used in command line as `mycommand 1 2 3 --flag`, you can also just type `-h` to check the detailed help info.

The command line documentation will be generated automatically from your Julia docstring.

If you have deeper hierachy of commands, you can also put `@cast` on a Julia module.

```julia
using Comonicon
@cast module NodeCommand

using Comonicon

@cast module NodeSubCommand
using Comonicon
@cast bar(x) = println("bar $x")
end
@cast foo(x) = println("foo $x")
@main
end

NodeCommand.command_main()
```
