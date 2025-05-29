```
set_configuration!(mvis::MechanismVisualizer, args...)
```

メカニズムビジュアライザーの設定を行い、再描画します。

# 例

```julia-repl
julia> set_configuration!(vis, [1., 2., 3.])
```

```julia-repl
julia> set_configuration!(vis, findjoint(robot, "shoulder"), 1.0)
```
