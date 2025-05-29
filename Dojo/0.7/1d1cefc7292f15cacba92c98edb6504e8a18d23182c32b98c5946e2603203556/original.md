```
Translational{T} <: Joint{T}

constraint limiting translational degrees of freedom

axis: translational axis in parent offset frame
axis_mask1: translational axis mask in pbody's frame
axis_mask2: translational axis mask in pbody's frame
axis_mask3: translational axis mask in pbody's frame
vertices: points in parent can child frames
spring: coefficient for joint spring
damper: coefficient for joint damper
spring_offset: nominal joint configuration
joint_limits: lower and upper limits on the joint configuration
spring_type: can be :linear or :sinusoidal (currently not implemented), if linear then we need joint_limits to avoid the 360° singularity.
input: external impulse force
```
