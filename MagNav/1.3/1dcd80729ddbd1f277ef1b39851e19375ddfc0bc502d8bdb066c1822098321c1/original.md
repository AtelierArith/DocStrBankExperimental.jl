```
fdm(x::Vector; scheme::Symbol = :central)
```

Finite difference method (FDM) applied to `x`.

**Arguments:**

  * `x`:      data vector
  * `scheme`: (optional) finite difference method scheme used

      * `backward`:  1st derivative 1st-order backward difference
      * `forward`:   1st derivative 1st-order forward  difference
      * `central`:   1st derivative 2nd-order central  difference
      * `backward2`: 1st derivative 2nd-order backward difference
      * `forward2`:  1st derivative 2nd-order forward  difference
      * `fourth`:    4th derivative central difference

**Returns:**

  * `dif`: vector of finite differences (length of `x`)
