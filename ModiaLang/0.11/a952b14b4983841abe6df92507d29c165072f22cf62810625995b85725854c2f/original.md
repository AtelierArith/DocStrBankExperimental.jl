```
path = PTP_path(names; positions, v_max, a_max, startTime=0.0)
```

Generate a new path object to move as fast as possible from positions[i,:] to positions[i+1,:]. The `positions[i,:]` can be a set of translational positions in [m], that is absolute distances, and/or rotational positions in  [rad] that is angles. In robotics such a movement is called PTP (Point-To-Point). The signals are constructed in such a way that it is not possible to move faster, given the maximally allowed velocity `v_max[j]` and the maximally allowed acceleration `a_max[j]` for signal `names[j]` and have a velocity of zero at the given `positions`.

If there are two or more signals (that is length(names) > 1) then the path is constructed such that all signals are in the same periods in the acceleration, constant velocity and deceleration phase. This means that only one of the signals is at its limits whereas the others are synchronized in such a way that the end point is reached at the same time instant.

For example, this means that the signals have a velocity of zero at positions[1,:], one of the signals is accelerated with its maximally allowed acceleration until one of the signals reaches its maximally allowed velocity. At a proper time instant, one of the signals is decelerated with the negative value of its maximally allowed acceleration, so that all signals reach positions[2,:] with velocity zero.

This element is useful to generate a reference signal for a controller which controls, e.g., a drive train, or to drive a flange according to a given acceleration.

# Example

```julia
using ModiaLang
@usingModiaPlot

const ptp_path = PTP_path(["angle1", "angle2", "angle3"],
                          positions = [0.0 2.0 3.0;  # angle1=0.0, angle2=2.0, angle3=3.0
                                       0.5 3.0 4.0;
                                       0.8 1.5 0.3;
                                       0.2 1.5 0.8],
                          startTime = 0.1,
                          v_max = 2*ones(3),
                          a_max = 3*ones(3))
angles = zeros(3)
getPosition!(ptp_path, 0.5, angles)   # angles = [0.12, 2.24, 3.24]
path = getPath(ptp_path)
plot(path, ["angle1", "angle2", "angle3"])
```
