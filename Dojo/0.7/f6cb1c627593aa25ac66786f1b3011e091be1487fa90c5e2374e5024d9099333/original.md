```
contact_constraint(bodies::Vector{Body}) 

generate ContactConstraints for each Body in list

normals: surface normal for each contact point
friction_coefficients: value of coefficient of friction for each contact point (optional for ImpactContact)
contact_origins: the offset with respect to the center of Body for each contact point (optional)
contact_radius: radius for each contact (optional)
contact_type: :nonlinear, :linear, :impact
```
