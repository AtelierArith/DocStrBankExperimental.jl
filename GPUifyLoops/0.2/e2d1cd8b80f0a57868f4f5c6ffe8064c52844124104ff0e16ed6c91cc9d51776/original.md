```
@loop for i in (A; B)
    # body
end
```

Take a `for i in (A; B)` expression and on the CPU lowers it to:

```julia
for i in A
    # body
end
```

and on the GPU:

```julia
for i in B
    if !(i in A)
        continue
    end
    # body
end
```
