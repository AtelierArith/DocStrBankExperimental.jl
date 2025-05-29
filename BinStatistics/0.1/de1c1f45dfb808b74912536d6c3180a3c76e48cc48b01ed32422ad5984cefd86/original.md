```
binstats(df, axis_col, axis_edges, bin_col; 
    grp_function = [nrow], col_function = [mean], missing_bin = false)
```

Returns a DataFrame containing function values for binned variables of `df`.

# Arguments

  * `axis_col`: binning axes column(s)
  * `axis_edges`: bin edges for `axis_col`
  * `bin_col`: column variable(s) to be binned
  * `grp_function = [nrow]`: column independent funciton(s) to be applied at group level
  * `var_function = [mean]`: column dependent funciton(s) to be applied to `bin_col` at group level
  * `missing_bin = false`: include missing bins

# Examples

```jldoctest julia> df = DataFrame(x=sin.(0:0.01:100), y = cos.(0:0.01:100), v1 = 0:0.01:100, v2 = (0:0.01:100).^2)

# bin as a function of `x` and return the `nrow` and `mean` of `v1` within each bin. `x` labels are bin centers

julia> binstats(df, :x, [-1, -.5, -0.25, 1], :v1) 3×3 DataFrame  Row │ x        nrow   v1_mean       │ Float64  Int64  Float64  ─────┼─────────────────────────    1 │  -0.75    3350  51.8438    2 │  -0.375    841  50.2257    3 │   0.375   5810  48.9042

# bin as a function of `x` and `y` nd return the `nrow` and `mean` of `v1` within each bin

julia> binstats(df, [:x, :y], [[-1, -.5, -0.25, 1], [-1, 0, 1]], [:v1]) 6×4 DataFrame  Row │ x        y        nrow   v1_mean       │ Float64  Float64  Int64  Float64  ─────┼──────────────────────────────────    1 │  -0.75      -0.5   1676  51.3281    2 │  -0.75       0.5   1674  52.36    3 │  -0.375     -0.5    434  50.7117    4 │  -0.375      0.5    407  49.7075    5 │   0.375     -0.5   2918  49.6149    6 │   0.375      0.5   2891  48.2039

# bin as a function of `x` and `y` and return the `mean` of `v1` and the `std` of `v2` within each bin

julia> binstats(df, [:x, :y], [[-1, -.5, -0.25, 1], [-1, 0, 1]], [:v1, :v2], grp*function = [], col*function = [mean, std]) 6×4 DataFrame  Row │ x        y        v1*mean  v2*std        │ Float64  Float64  Float64  Float64  ─────┼────────────────────────────────────    1 │  -0.75      -0.5  51.3281  3067.6    2 │  -0.75       0.5  52.36    3123.3    3 │  -0.375     -0.5  50.7117  3025.52    4 │  -0.375      0.5  49.7075  2790.1    5 │   0.375     -0.5  49.6149  2970.39    6 │   0.375      0.5  48.2039  2864.74

# bin as a function of `x` and `y` and return the `mean` and `std` of both `v1` and `v2` within each bin

# NOTE: `col_function` from changed `Vector` to `Matrix`, i.e. comma removed from col_function

julia> binstats(df, [:x, :y], [[-1, -.5, -0.25, 1], [-1, 0, 1]], [:v1, :v2], grp*function = [], col*function = [mean std]) 6×6 DataFrame  Row │ x        y        v1*mean  v2*mean  v1*std   v2*std        │ Float64  Float64  Float64  Float64  Float64  Float64  ─────┼──────────────────────────────────────────────────────    1 │  -0.75      -0.5  51.3281  3474.45  28.9892  3067.6    2 │  -0.75       0.5  52.36    3579.9   28.9626  3123.3    3 │  -0.375     -0.5  50.7117  3407.85  28.9501  3025.52    4 │  -0.375      0.5  49.7075  3210.43  27.2289  2790.1    5 │   0.375     -0.5  49.6149  3300.65  28.9707  2970.39    6 │   0.375      0.5  48.2039  3149.59  28.7447  2864.74
