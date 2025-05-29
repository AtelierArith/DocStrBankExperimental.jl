```julia
begin_supplemental_attributes_update(
    func::Function,
    sys::PowerSystems.System
) -> Any

```

Begin an update of supplemental attributes. Use this function when adding or removing many supplemental attributes in order to improve performance.

If an error occurs during the update, changes will be reverted.

# Examples

```julia
begin_supplemental_attributes_update(sys) do
    add_supplemental_attribute!(sys, component1, attribute1)
    add_supplemental_attribute!(sys, component2, attribute2)
end
```
