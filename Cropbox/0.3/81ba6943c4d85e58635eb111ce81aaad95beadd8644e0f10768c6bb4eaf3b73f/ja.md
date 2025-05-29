```
Config
```

システムの設定のセットを含みます。システムの設定にはパラメータ値が含まれます。

# 例

```julia-repl
julia> @config :S => :a => 1
Config for 1 system:
  S
    a = 1
```

参照: [`@config`](@ref)
