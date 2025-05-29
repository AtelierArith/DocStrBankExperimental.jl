```
subnetworks(rn::ReactionSystem)
```

反応ネットワークの各連結クラスに対応するサブネットワークを見つけます。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
subnetworks(sir)
```
