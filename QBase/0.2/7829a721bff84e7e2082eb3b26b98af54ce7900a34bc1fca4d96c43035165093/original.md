```
qubit_rotation( θ :: Real; axis="x" :: String ) :: Unitary{Complex{Float64}}
```

Returns a unitary which performs a qubit rotation along bloch sphere. `θ` designates the angle of rotation and `axis` (`"x"`, `"y"`, `"z"`) designates the cartesian axis about which the qubit is rotated.
