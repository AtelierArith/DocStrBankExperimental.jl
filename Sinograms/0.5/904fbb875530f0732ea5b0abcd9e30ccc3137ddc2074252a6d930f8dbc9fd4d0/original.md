```
image = fdk(plan, proj)
```

Reconstruct 3D image from cone-beam computed tomography (CBCT) data collected with a circular source trajectory via FDK method.

# in

  * `plan::FDKplan`
  * `proj` (ns,nt,na) projection views

# out

  * `image` (nx,ny,nz) reconstructed image

References: Feldkamp, Davis, Kress, JOSA-A, 1(6):612-9, June 1984.
