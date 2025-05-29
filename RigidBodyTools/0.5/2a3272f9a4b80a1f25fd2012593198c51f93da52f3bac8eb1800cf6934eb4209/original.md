```
joint_transform(q::AbstractVector,joint::Joint)
```

Use the joint dof entries in `q` to create a joint transform operator. The number of entries in `q` must be apprpriate for the type of joint `joint`.
