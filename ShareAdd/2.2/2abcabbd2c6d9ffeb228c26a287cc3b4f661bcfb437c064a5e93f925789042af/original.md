```
@showenv
@showenv item
```

Open (shared) environment folder in your desktop GUI. The utility of this macro is that it makes it easy to access these folders in your OS, which might otherwise require some jumping through hoops, as these are located in the hidden folder ~/.julia/

This macro is exported.

# Examples

```julia-repl
julia> @showenv # called without arguments, opens the "environments" folder which contains all shared environments
julia> @showenv Revise # open the environment folder(s) which contain the Revise package
julia> @showenv "Revise" # both quoted and unquoted forms of the argument are OK
julia> @showenv Math # opens the folder of the shared env @Math
```
