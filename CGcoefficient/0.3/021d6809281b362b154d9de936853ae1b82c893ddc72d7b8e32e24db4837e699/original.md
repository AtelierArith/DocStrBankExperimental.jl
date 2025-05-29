```
wigner_init_float(n::Integer, mode::AbstractString, rank::Integer)
```

We calculate the Wigner Symbols with binomials. We will store some binomials first, then when we need one binomial, we just load it. In this package, the functions starts with `f` character dependent on the stored binomials. The `wigner_init_float` function is used to extend the range of the stored binomial table.

The parameters means:

  * `mode`:

      * `"Jmax"`: set the maximum angular momentum in the system.
      * `"2bjmax"`: set the maximum two-body coupled angular momentum in the system.
      * `"nmax"`: directly set the maximum binomial number.
      * `"Moshinsky"`: set the maximum `N = 2n+l` in the Moshinsky bracket.
  * `n`: the maximum angular momentum or the maximum binomial number, dependent on the `mode`.
  * `rank`:

      * `3`: calculate only CG coefficients and 3j symbols.
      * `6`: calculate CG coefficients, 3j symbols and 6j symbols.
      * `9`: calculate CG coefficients, 3j symbols, 6j symbols and 9j symbols.

`"Jmax"` means the global maximum angular momentum, for every parameters. It is always safe with out any assumption.

The `"2bjmax"` mode means your calculation only consider two-body coupling, and no three-body coupling. This mode assumes that in all these coefficients, at least one of the angular momentun is just a single particle angular momentum. With this assumption, `"2bjmax"` mode will use less memory than `"Jmax"` mode.

The `"Moshinsky"` mode means you want to calculate the Moshinsky brackets. The `n` parameter is the maximum `N = 2n+l` in the Moshinsky bracket. The `rank` parameter is ignored.

The `"nmax"` mode directly set `nmax`, and the `rank` parameter is ignored. 

For example

```julia
wigner_init_float(21, "Jmax", 6)
```

means you calculate CG and 6j symbols, and donot calculate 9j symbol. The maximum angular momentum in your system is 21.

The exact values of the maximum `nmax` for different `rank` are shown in the table below ([details](https://0382.github.io/CGcoefficient.jl/stable/wigner/#Estimate-the-capacity)).

|                                       | Calculate range |  CG & 3j  | 6j & Racah |    9j     |
|:-------------------------------------:|:---------------:|:---------:|:----------:|:---------:|
|           meaning of `type`           |  `type`\`rank`  |     3     |     6      |     9     |
|         max angular momentum          |    `"Jmax"`     | `3Jmax+1` | `4Jmax+1`  | `5Jmax+1` |
| max two-body coupled angular momentum |   `"2bjmax"`    | `2jmax+1` | `3jmax+1`  | `4jmax+1` |
| max $N = 2n+l$ for Moshinsky bracket  |  `"Moshinsky"`  | `6Nmax+1` | `6Nmax+1`  | `6Nmax+1` |
|             max binomial              |    `"nmax"`     |  `nmax`   |   `namx`   |  `nmax`   |

You do not need to rememmber those values in the table. You just need to find the maximum angular momentum in you canculation, then call the function.

The `wigner_init_float` function is **not** thread safe, so you should call it before you start your calculation.
