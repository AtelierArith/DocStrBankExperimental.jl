```
@config c.. -> Config | Vector{Config}
```

Construct a set or multiple sets of configuration.

A basic unit of configuration for a system `S` is represented by a pair in the form of `S => pv`. System name `S` is expressed in a symbol. If actual type of system is used, its name will be automatically converted to a symbol.

A parameter name and corresponding value is then represented by another pair in the form of `p => v`. When specifiying multiple parameters, a tuple of pairs like `(p1 => v1, p2 => v2)` or a named tuple like `(p1 = v1, p2 = v2)` can be used. Parameter name must be a symbol and should indicate a variable declared with `parameter` tag as often used by `preserve` state variable. For example, `:S => (:a => 1, :b => 2)` has the same meaning as `S => (a = 1, b = 2)` in the same scope.

Configurations for multiple systems can be concatenated by a tuple. Multiple elements in `c` separated by commas implicitly forms a tuple. For example, `:S => (:a => 1, :b => 2), :T => :x => 1` represents a set of configuration for two systems `S` and `T` with some parameters. When the same names of system or variable appears again during concatenation, it will be overriden by later ones in an order appeared in a tuple. For example, `:S => :a => 1, :S => :a => 2` results into `:S => :a => 2`. Instead of commas, `+` operator can be used in a similar way as `(:S => :a => 1) + (:S => :a => 2)`. Note parentheses placed due to operator precedence.

When multiple sets of configurations are needed, as in `configs` for [`simulate`](@ref), a vector of `Config` is used. This macro supports some convenient ways to construct a vector by composing simpler configurations. Prefix operator `!` allows *expansion* of any iterable placed in the configuration value. Infix operator `*` allows *multiplication* of a vector of configurations with another vector or a single configuration to construct multiple sets of configurations. For example, `!(:S => :a => 1:2)` is expanded into two sets of separate configurations `[:S => :a => 1, :S => :a => 2]`. `(:S => :a => 1:2) * (:S => :b => 0)` is multiplied into `[:S => (a = 1, b = 0), :S => (a = 2, b = 0)]`.

# Examples

```julia-repl
julia> @config :S => (:a => 1, :b => 2)
Config for 1 system:
  S
    a = 1
    b = 2
```

```julia-repl
julia> @config :S => :a => 1, :S => :a => 2
Config for 1 system:
  S
    a = 2
```

```julia-repl
julia> @config !(:S => :a => 1:2)
2-element Vector{Config}:
 <Config>
 <Config>
```

```julia-repl
julia> @config (:S => :a => 1:2) * (:S => :b => 0)
2-element Vector{Config}:
 <Config>
 <Config>
```
