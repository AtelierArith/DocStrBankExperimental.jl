```
MassProp(m, Ixx, Iyy, Izz, Ixz, Ixy, Iyz)
```

Mass and moments of inertia in the body frame. Ixx = int(y^2 + z^2, dm) Ixz = int(xz, dm)

Most aircraft are symmetric about y and so there is a convenience method  to specify only the nonzero components. MassProp(m, Ixx, Iyy, Izz, Ixz)
