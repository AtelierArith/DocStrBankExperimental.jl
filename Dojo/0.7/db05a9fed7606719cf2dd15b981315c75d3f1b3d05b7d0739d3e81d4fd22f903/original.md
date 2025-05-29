```
Rotational{T} <: Joint{T}

constraint limiting rotational degrees of freedom

axis: rotation axis in parent offset frame
axis_mask1: rotation axis mask in pbody's frame
axis_mask2: rotation axis mask in pbody's frame
axis_mask3: rotation axis mask in pbody's frame
orientation_offset: rotation axis offset from pbody's frame
spring :coefficient for joint spring
damper: coefficient for joint damper
spring_offset: nominal joint configuration
joint_limits: lower and upper limits on the joint configuration
spring_type: can be :linear or :sinusoidal (currently not implemented), if linear then we need joint_limits to avoid the 360° singularity.
input: external impulse torque
```
