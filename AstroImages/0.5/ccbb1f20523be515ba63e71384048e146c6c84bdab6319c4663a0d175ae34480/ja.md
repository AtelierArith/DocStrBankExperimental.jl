HISTORYヘッダーエントリへのアクセスと設定を可能にします

```julia
img = AstroImage(randn(10,10))
push!(img, History, "2023-04-19: Added history entry.")
img[History] # ["2023-04-19: Added history entry."]
```
