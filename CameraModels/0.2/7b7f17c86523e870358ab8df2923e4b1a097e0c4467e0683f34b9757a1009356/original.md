```julia
intersectRayToPlane(
    c_H_a,
    a_F,
    l_nFL,
    l_FL;
    M,
    R0,
    l_T_ex,
    ex_T_c
)

```

Ray trace from pixel coords to a floor in local level reference which is assumed  aligned with gravity.  Returns intersect in local level frame (coordinates).

Notes

  * Implemented against local level to allow easier local or world reference usage,

      * Just assume world is local level, i.e. `l_nFL = w_nFL` and `l_FL = w_FL`.
      * User must provide (assumed dynamic) local level transform via `l_T_ex` – see example below!
  * Coordinate chain used is from ( pixel-array (a) –> camera (c) –> extrinsic (ex) –> level (l) )

      * `c_H_a` from pixel-array to camera (as homography matrix)
      * `a_F` feature in array pixel frame
      * `l_T_ex` extrinsic in body (or extrinsic to local level), SE3 Manifold element using ArrayPartition
      * `ex_T_c` camera in extrinsic (or camera to extrinsic)
  * line-to-plane intersect computation done in the local level frame

Example

```
# Assume body coords x,y,z == fwd,prt,upw

# Camera setup
f = 800.0        # pixels
ci,cj = 360,640  # assuming 720x1280 image
# going from imaging array to camera frame
c_H_a = [0 1 -cj; 1 0 -ci; 0 0 f] # camera matrix

# body to extrinsic of camera -- e.g. camera looking down 0.2 and left 0.2
# local level to body to extrinsic transform 
l_T_b = ArrayPartition([0;0;0.], R0)
b_T_ex = ArrayPartition([0;0;0.], exp_lie(Mr, hat(Mr, R0, [0;0.2;0.2])))
l_T_ex = compose(M, l_T_b, b_T_ex) # this is where body reference is folded in.

# FLOOR in local level coordinates, normal and point
l_nFL = [0; -0.05; 1.]
l_FL = [0; 0; -2.]

# Ray trace to plane
l_Forb = intersectRayToPlane(
  c_H_a,
  a_Forb,
  l_nFL,
  l_FL;
  l_T_ex
)
```

See also: `CameraModels.intersectLineToPlane3D`
