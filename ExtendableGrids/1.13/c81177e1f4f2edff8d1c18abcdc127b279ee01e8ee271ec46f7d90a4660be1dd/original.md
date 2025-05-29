```julia
geomspace(a, b, ha, hb; tol, maxiterations) -> Any

```

(Try to) create a subdivision of interval (a,b) stored in the  returned array X such that 

  * `X[1]==a, X[end]==b`
  * `(X[2]-X[1])<=ha+tol*(b-a)`
  * `(X[end]-X[end-1])<=hb+tol*(b-a)`
  * There is a number q such that  `X[i+1]-X[i] == q*(X[i]-X[i-1])`
  * X is the array with the minimal possible number of points with the above property

Caveat: the algorithm behind this is  tested for many cases but unproven.

Returns an Array containing the points of the subdivision.
