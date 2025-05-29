```
function UniformBZMesh(; br::Cell, origin, size, shift)
```

customized constructor for UniformBZMesh. The parameters origin and shift is provided to customize the mesh as Gamma-centered or M-P mesh. 

# Parameters:

  * `cell`: Cell info
  * `origin`: a number indicating shift of origin.    the actuall origin becomes origin*(b1+b2+b3)   default value origin=-1/2 takes (0,0,0) to center of 1st BZ, origin=0 makes mesh[1,1,1]=(0,0,0)+shift
  * `size`: size of the mesh
  * `shift`: additional k-shift for mesh points.    actuall shift is shift*(b1/N1+b2/N2+b3/N3)   for even N, shift=1/2 avoids high symmetry points while preserve symmetry.
