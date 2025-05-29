```
glue(Fs::Vararg{T}) where {T<:Flag}
```

Glues Flags together "on top of each other". Optionally specifices the output Flag type, for cases where a different type may improve performance (E.g. non-induced Flag as target for the gluing of two induced Flags). The default implementation only uses the custom type for the final gluing.

```
glue(F, G, H)
```

is equivalent to

```
glue(F, glue(G, H, 1:size(G)), 1:size(F))
```
