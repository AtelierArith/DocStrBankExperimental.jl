```
@setpkg command[ command-arguments... ]
```

The @setpkg macro enables sharing sets among developers and users.

# commands

## load: loads sets from a local file, also known as a setfile

```
@setpkg load <path/to/file>
```

The setfile is a regular Julia module customized for SetBuilders.

# Examples

Assuming that the file `myset.sjl` contains the following Julia code:

```julia
module MySetModule

export MYSET

I = @setbuild(Integer)
MYSET = @setbuild(x in I, x > 0)

end
```

`MYSET` can be used as shown in the example below:

```julia-repl
julia> @setpkg load "myset.sjl"

julia> using SetBuilders.MySetModule

julia> 1 in MYSET
true

julia> 0 in MYSET
false
```

!!! note
    keyword names starting with "sb_" are reserved for SetBuilders internal uses.

