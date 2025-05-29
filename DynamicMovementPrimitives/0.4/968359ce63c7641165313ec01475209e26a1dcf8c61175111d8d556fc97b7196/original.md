Same as DMP but contains an extra struct `opts2` with 2DOF controller parameters Upgrade a `DMP` to a `DMP2dof` using

```  dmp2opts = DMP2dofopts(kp = 25,kv = 10,kc = 10_000,αe = 5) # Specify parameters here

dmp2 = DMP2dof(dmp, dmp2opts) # Upgrade dmp to 2DOF version  ```
