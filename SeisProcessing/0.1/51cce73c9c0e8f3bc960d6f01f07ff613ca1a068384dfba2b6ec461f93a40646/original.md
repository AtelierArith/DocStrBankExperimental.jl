```
SeisRadon_tx(In,Par,itype);
```

RADON_FX: Operators for f-x, tau-p forward and adjoint Radon transforms           to compute linear or  parabolic Radon transform. IN    Radon coefficients if itype =  1 (Forward transform)  with In(np,nt)       CMP gather         if itype = -1 (Adjoint transform)  with In(nh,nt)

OUT   CMP gather         if itype =  1 (Forward transform)  with Out(nh,nt)       Radon coeffcients  if itype = -1 (Adjoint transform)  with Out(np,nt)

# Parameters

  * `Par.h`:vector containing the nh offsets
  * `Par.p`:vector containing the np curvatures normalized by far offset (s) if itype='parab'
  * `Par.p`:vector containing the np dips in s/m if itype='linear'
  * `Par.dt`:sampling interval
  * `Par.f`:frequency corners of BP operator - this acts like a zero phase wavelet.
  * `Par.transf`:'parab', 'linear', 'hyperb'

itype =  1  :  forward itype = -1  :  adjoint
