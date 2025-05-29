```
Pipelines(pipeline...)
```

`Pipeline`のチェーン。

# 例

```julia-repl
julia> pipes = Pipelines(Pipeline{:x}((x,y)->x), Pipeline{(:sinx, :cosx)}((x,y)->sincos(x)))
Pipelines:
  target[x] := var"#25#27"()(source, target)
  target[(sinx, cosx)] := var"#26#28"()(source, target)

julia> pipes(0.3)
(x = 0.3, sinx = 0.29552020666133955, cosx = 0.955336489125606)

# または `|>` を使用
julia> pipes = Pipeline{:x}((x,y)->x) |> Pipeline{(:sinx, :cosx)}((x,y)->sincos(x))
Pipelines:
  target[x] := var"#29#31"()(source, target)
  target[(sinx, cosx)] := var"#30#32"()(source, target)

julia> pipes(0.3)
(x = 0.3, sinx = 0.29552020666133955, cosx = 0.955336489125606)

```
