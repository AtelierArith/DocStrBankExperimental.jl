```
x = fminbnd(f, ax, bx,  tol)


an approximation  x  to the point where  f  attains a minimum  on
```

the interval  (ax,bx)  is determined.

input..

f     function subprogram which evaluates  f(x)  for any  x       in the interval  (ax,bx) ax    left endpoint of initial interval bx    right endpoint of initial interval tol   desired length of the interval of uncertainty of the final       result ( .ge. 0.0d0)

output..

fmin  abcissa approximating the point where  f  attains a minimum

```
the method used is a combination of  golden  section  search  and
```

successive parabolic interpolation.  convergence is never much slower than  that  for  a  fibonacci search.  if  f  has a continuous second derivative which is positive at the minimum (which is not  at  ax  or bx),  then  convergence  is  superlinear, and usually of the order of about  1.324....     the function  f  is never evaluated at two points closer together than  eps*abs(fmin) + (tol/3), where eps is  approximately the square root  of  the  relative  machine  precision.   if   f   is a unimodal function and the computed values of   f   are  always  unimodal  when separated by at least  eps*abs(x) + (tol/3), then  fmin  approximates the abcissa of the global minimum of  f  on the interval  ax,bx  with an error less than  3*eps*abs(fmin) + tol.  if   f   is not unimodal, then fmin may approximate a local, but perhaps non-global, minimum to the same accuracy.     this function subprogram is a slightly modified  version  of  the algol  60 procedure  localmin  given in richard brent, algorithms for minimization without derivatives, prentice - hall, inc. (1973).

### 

Rewrite in Julia of [fmin from Netlib](http://www.netlib.org/fmm/fmin.f) by Mikhail Kagalenko, January 2024
