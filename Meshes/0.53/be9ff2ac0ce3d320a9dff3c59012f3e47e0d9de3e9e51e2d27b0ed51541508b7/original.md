```
angles(chain)
```

Return angles `∠(vᵢ-₁, vᵢ, vᵢ+₁)` at all vertices `vᵢ` of the `chain`. If the chain is open, the first and last vertices have no angles. Positive angles represent a CCW rotation whereas negative angles represent a CW rotation. In either case, the absolute value of the angles returned is never greater than `π`.
