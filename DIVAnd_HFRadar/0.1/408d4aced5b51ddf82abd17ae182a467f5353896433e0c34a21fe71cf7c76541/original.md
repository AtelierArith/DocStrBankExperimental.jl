```
DIVAndrun_HFRadar(mask,h,pmn,xyi,xyobs,robs,directionobs,len,epsilon2;...)
```

HF Radar current analysis with DIVAnd and velocity constraints. The input parameters are:

  * `mask`: true for sea points (false for land points) (3D-array)
  * `h`: depth in meters (3D-array)
  * `pmn`: inverse of the local resolution (tuple of three 3D-arrays)
  * `xyi`: coordinates of the analysis grid (tuple of three 3D-arrays)
  * `xyobs`: coordinates of the observations (tuple of three vectors)
  * `robs`: radial velocity (vector)
  * `directionobs`: angle α of the measured direction in *degrees* (vector) such that (see below)

$$
u_{obs}  \sin(α) + v_{obs}  \cos(α) ≈ r_{obs}
$$

  * `len`: the correlation length (a tuple of scalars)
  * `epsilon2`: error variance of the observation relative to the error variace of

the background estimate.

## Optional input parameters

  * `eps2_boundary_constraint` (default -1): rel. error variance of the boundary constraints
  * `eps2_div_constraint` (default -1): rel. error variance of the divergence constraints
  * `eps2_Coriolis_constraint` (default -1): rel. error variance of the Coriolis constraints
  * `f` (default 0.001 s⁻¹): Coriolis parameter. For a latitude $φ$, we have on Earth :

$$
\begin{aligned}
    Ω =& 7.2921 \; 10^{-5} rad/s \\
    f =& 2 Ω \sin(φ)
\end{aligned}
$$

  * `g` (default 0. m/s²): acceleration due to gravity. If g is zero, then the surface pressure is not considered; otherwise g should be set to 9.81.
  * `ratio` (default 100): normalization factor
  * `lenη`  (default 0, 0, 24 * 60 * 60. * 10): correlation length in space and time for the surface elevation
  * `residual`: an array of the same size as robs with the residual (output)

## Convention for the direction

The bearing β is the angle at radar station (*) between North a measuring point (+) counted clockwise and the direction α is angle at measuring point between North and vector pointing to the radar station counted clockwise

```
                ↑ /
                |/
         ↑      +--→ current vector (u,v)
  North  |     / measurent point
         |    /
         |   /
         |  /
         |β/
         |/
         *
   radar station
```

Sufficiently far from the poles, we have:

$$
α ≈ β + 180°
$$

The $u$ zonal and $v$ meridional velocity component are related to the radial current $r$ and direction $lpha$ by:

$$
\begin{aligned}
u =& r \sin(α) \\
v =& r \cos(α) \\
\end{aligned}
$$

$$
\begin{aligned}
r =& u  \sin(α) + v  \cos(α) \\
\tan(α) &= {u \over v}
\end{aligned}
$$

For HF radar data, r is positive if the velocity is pointing *towards* the radar site. r, u, v, direction and β consistent with the CODAR convention of the ruv files [1,2]:

> A positive radial velocity is moving towards the SeaSonde, while a negative radial velocity is moving away from the SeaSonde.


!!! note
    For the Coriolis force constrain and the surface pressure gradient constrain, one need to include a time dimension.


!!! info
    On input, the direction angles $lpha$ are expressed in degrees (0 - 360°)


!!! info
    If you see the error `ERROR: PosDefException: matrix is not positive definite; Cholesky factorization failed.` you might need to check the values of your input parameters, in particular correlation, scale factors `pmn` and `epsilon2`.


[1] [File Formats Used for CODAR Radial Data](https://web.archive.org/web/20181009090405/https://cordc.ucsd.edu/projects/mapping/documents/radFileFormats_20050408.pdf)

[2] [Technicians Information Page for SeaSondes](https://web.archive.org/web/20200125080518/http://support.codar.com/Technicians_Information_Page_for_SeaSondes/Docs/GuidesToFileFormats/File_LonLatUV_RDL_TOT_ELP.pdf)
