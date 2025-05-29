```
ray_class_field(m::MapClassGrp) -> ClassField
ray_class_field(m::MapRayClassGrp) -> ClassField
```

Creates the (formal) abelian extension defined by the map $m: A \to I$ where $I$ is the set of ideals coprime to the modulus defining $m$ and $A$ is a quotient of the ray class group (or class group). The map $m$ must be the map returned from a call to {class*group} or {ray*class_group}.
