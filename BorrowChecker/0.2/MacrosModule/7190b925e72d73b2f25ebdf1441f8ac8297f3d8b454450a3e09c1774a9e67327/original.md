```
@lifetime a begin
    @ref ~a rx = x
    # use refs here
end
```

Create a lifetime scope for references. References created with this lifetime are only valid within the block and are automatically cleaned up when the block exits.
