```
RigidBodyMotion
```

Type containing the connectivities and motions of rigid bodies, linked to the inertial system and possibly to each other, via joints. The basic constructor is `RigidBodyMotion(joints::Vector{Joint},nbody::Int)`, in which `joints` contains a vector of joints of [`Joint`](@ref) type, each specifying the connection between a parent and a child body. (The parent may be the inertial coordinate system.)
