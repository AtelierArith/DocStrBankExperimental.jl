```
ind2sub(io, i)
```

Return the (frame,volume...) tuple for the liner index `i`.  This is useful for looping over all frames in a data-set that is more that 4 or more dimensions. For example,

```julia
for i = 1:length(io)
    trcs, hdrs = readframe(io, ind2sub(io,i)...)
end
```
