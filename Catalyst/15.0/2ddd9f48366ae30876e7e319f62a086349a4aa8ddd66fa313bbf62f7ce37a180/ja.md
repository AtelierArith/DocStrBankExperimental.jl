```
linkageclasses(rn::ReactionSystem)
```

反応ネットワークのインシデンスグラフを考慮して、グラフの連結成分のベクトルを返します（すなわち、インシデンスグラフで接続されている反応複合体のサブグループ）。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
linkageclasses(sir)
```

は次のようになります。

```julia
2-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
```
