```
isreversible(rn::ReactionSystem)
```

反応ネットワークが与えられた場合、そのネットワークが可逆かどうかを返します。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
isreversible(sir)
```
