```
FieldArray(
    fr::FieldRecord; 
    expand_cartesian=true, 
    omit_recorddim_if_constant=true,
    lookup_coords=true,
    coords=nothing,
)
```

Construct [`FieldArray`](@ref) from all records in `fr::FieldRecord`

Provides a view of internal storage format of `FieldRecord` as an n-dimensional Array.

# Keyword arguments

  * `expand_cartesian`: (spatially resolved output using a `CartesianLinearGrid` only), `true` to expand compressed internal data (with spatial dimension `cells`) to a cartesian array  (with spatial dimensions eg `lon`, `lat`, `zt`)
  * `omit_recorddim_if_constant`: Specify whether to include multiple (identical) records and record dimension for constant variables  (with attribute `is_constant = true`). PALEO currently always stores these records in the input `fr::FieldRecord`;   set `false` include them in `FieldArray` output, `true` to omit duplicate records and record dimension from output.
  * `lookup_coords`: `true` to include coordinates, `false` to omit coordinates.
  * `coords`: replace the attached coordinates from the input `fr::FieldRecord` for one or more dimensions. Format is a Vector of Pairs of `"<dim_name>"=>("<var_name1>", "<var_name2>", ...)`,  eg to replace an nD column atmosphere model default pressure coordinate with a z coordinate:

    ```
    coords=["cells"=>("atm.zmid", "atm.zlower", "atm.zupper")]
    ```
