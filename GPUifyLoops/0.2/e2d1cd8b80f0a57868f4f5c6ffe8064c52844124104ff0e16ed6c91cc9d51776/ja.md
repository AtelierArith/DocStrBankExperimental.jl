```
@loop for i in (A; B)
    # body
end
```

`for i in (A; B)` の式を取ると、CPUでは次のように低下します：

```julia
for i in A
    # body
end
```

GPUでは：

```julia
for i in B
    if !(i in A)
        continue
    end
    # body
end
```
