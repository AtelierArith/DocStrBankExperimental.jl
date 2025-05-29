```
Dof(dof_id::Int,dof_type::String,stiff::Float64,damp::Float64,motion::Motions)
```

Set up a single degree of freedom(dof) information in a joint. A joint may have a maximum 6 dofs and minimum 1 dof(either active or passive). Here we don't allow it to have 0 since there's no reason to do this. If we want the parent body and child body to have no relative motion(i.e. they're rigidly connected together), we can set the second joint has only one dof and this dof has active "hold" motion.

## Fields

  * `dof_id`: Choose from 1 to 6 and is corresponding to [Ox, Oy, Oz, x, y, z].
  * `dof_type`: "passive" or "active"
  * `stiff`: Non-dimensional stiffness of a string associated with this degree of   freedom. Only has effect on solving the system when this dof is passive.
  * `damp`: Similar to stiff, this assigns the damping coefficient of this dof.
  * `motion`: Defines the motion of this dof. Refer to type `Motion`
