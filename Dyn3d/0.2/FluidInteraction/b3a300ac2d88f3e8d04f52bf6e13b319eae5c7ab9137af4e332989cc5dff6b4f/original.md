```
BodyGrid(bid::Int, np::Int, points, q_i, f_ex3d, f_ex6d)
```

Design this structure to contain body points coord, motion and forces used in fluid-structure interaction

## Fields

  * `bid`: body id in the joint-body chain
  * `np`: number of grid points on this body
  * `points`: (x,y,z) coordinates of all body points in local body frame
  * `q_i`: (x,y,z) coordinates of all body points in inertial frame
  * `v_i`: velocity of all body points in inertial frame
  * `f_ex3d`: external force in (x,y,z) (by fluid) on all body points in inertial frame
  * `m_ex3d`: external moment in (x,y,z) (by fluid) on all body points in inertial frame
  * `f_ex6d`: f_ex3d integrated through all body points on one body and described in 6d spatial vector form

## Constructors

  * `BodyGrid(bid,np,points)`: initialize q*i, v*i, f*ex3d, m*ex3d to be Vector of zeros(3),                            f_ex6d to be zeros(6)
