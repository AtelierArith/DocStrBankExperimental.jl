# Extended help

```
translate(H::Hyperrectangle, v::AbstractVector; [share]::Bool=false)
```

### Input

  * `H`     – hyperrectangle
  * `v`     – translation vector
  * `share` – (optional, default: `false`) flag for sharing unmodified parts of            the original set representation

### Notes

The radius vector is shared with the original hyperrectangle if `share == true`.
