```
Joint(jtype::AbstractJointType,parent_id,Xp_to_j::MotionTransform,child_id,Xch_to_j::MotionTransform,
        dofs::Vector{AbstractDOFKinematics};[params=Dict()])
```

Construct a joint of type `jtype`, connecting parent body of id `parent_id` to child body of id `child_id`. The placement of the joint on the bodies is given by `Xp_to_j` and `Xch_to_j`, the transforms from the parent and child coordinate systems to the joint system, respectively. Each of the degrees of freedom for the joint is specified with `dofs`, a vector of `AbstractDOFKinematics`. Any parameters required by the joint can be passed along in the optional `params` dictionary.
