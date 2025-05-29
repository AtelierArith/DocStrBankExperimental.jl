```
feedback2dof(P, C, F)
```

Return the transfer function `P(F+C)/(1+PC)` which is the closed-loop system with process `P`, controller `C` and feedforward filter `F` from reference to control signal (by-passing `C`).

```
         +-------+
         |       |
   +----->   F   +----+
   |     |       |    |
   |     +-------+    |
   |     +-------+    |    +-------+
r  |  -  |       |    |    |       |    y
+--+----->   C   +----+---->   P   +---+-->
      |  |       |         |       |   |
      |  +-------+         +-------+   |
      |                                |
      +--------------------------------+
```
