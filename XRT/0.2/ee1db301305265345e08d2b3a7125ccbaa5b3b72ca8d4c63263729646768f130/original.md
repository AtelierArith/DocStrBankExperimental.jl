```Julia
sync!(b::AbstractBOArray, direction::XRTWrap.BOSyncDirection.Type)
sync!(w::AbstractSyncDirectionWrapper, direction::XRTWrap.BOSyncDirection.Type)

```

Synchronise buffer content in specified direction. Use `BOArray` or `Array` with sync direction in type to prohibit a specific sync direction.
