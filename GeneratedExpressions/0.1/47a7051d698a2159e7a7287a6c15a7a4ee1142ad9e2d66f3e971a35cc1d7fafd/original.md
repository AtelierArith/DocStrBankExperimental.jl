```
@fileval <path> <global opts> <substitutions (singleton range)>
```

Expand and evaluate parametrized expression comprehensions in a file, and evaluate the resulting expression. Use `mode=string` to process the input as a string (which is then parsed and evaluated).

# Examples

```
@fileval "file.jl" mode=expr x=1 # treat contents of "file.jl" as expression (parse first, then expand)
@fileval file_string.jl mode=string x=1 # first expand as string, then 
```
