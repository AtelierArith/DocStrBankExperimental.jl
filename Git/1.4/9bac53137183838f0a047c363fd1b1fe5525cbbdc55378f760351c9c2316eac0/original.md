```
git()
```

Return a `Cmd` for running Git.

## Example

```julia
julia> run(`$(git()) clone https://github.com/JuliaRegistries/General`)
```

This can equivalently be written with explicitly split arguments as

```
julia> run(git(["clone", "https://github.com/JuliaRegistries/General"]))
```

to bypass the parsing of the command string.
