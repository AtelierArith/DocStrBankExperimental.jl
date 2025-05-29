```
collectConfig(config::String)
```

#### Example:

```
julia> collectConfig("[Be]2p¹") == ["1s↓0", "1s↑0", "2s↓0", "2s↑0", "2p↓-1"]
true

julia> julia> collectConfig("1s↑1s↓02p↑-1") == ["1s↑", "1s↓0", "2p↑-1"]
true
```
