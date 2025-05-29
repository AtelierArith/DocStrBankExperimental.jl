```
shoaling_approx(d, H, L; cc=2, N=10, g=9.81)
```

Calculate shoaling coefficients `K` in range of depth values `d` for wave of length `L` and height `H`.

# Arguments

  * `d`: vector of decreasing water depths (m)
  * `L`: initial wavelength (m) - corresponding to d[1]
  * `H`: initial wave height (m) - corresponding to d[1]
  * `cc`: current criterion; `cc=1` - Stokes, `cc=2` - Euler (default)
  * `N`: number of solution eigenvalues, defaults to `N=10`
  * `g`: gravity acceleration (m/s^2), defaults to `g=9.81`

# Output

  * `K`: vector of shoaling coefficient values
