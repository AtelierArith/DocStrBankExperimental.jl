```
extractCore(config::String)
```

Extract *core configuration* from `config` given in *compact configuration notation*

#### Example

```
julia> extractCore("[Ar]4s¹")
"1s²2s²2p⁶3s²3p⁶"
```
