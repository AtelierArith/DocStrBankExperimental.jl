```julia
tagOrthogonalIteration(
    corners,
    H,
    f_width,
    f_height,
    c_width,
    c_height;
    taglength,
    nIters
)

```

Run the orthoganal iteration algorithm on the poses. 

Notes

  * See apriltag_pose.h
  * [2]: Lu, G. D. Hager and E. Mjolsness, "Fast and globally convergent pose estimation from video images,"  in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 22, no. 6, pp. 610-622, June 2000.  doi: 10.1109/34.862199
  * The low level C-library uses `fx=f_width`.
