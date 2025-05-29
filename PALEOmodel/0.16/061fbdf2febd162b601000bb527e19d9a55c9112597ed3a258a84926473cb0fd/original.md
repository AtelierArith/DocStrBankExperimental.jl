```
get_array(
    fr::FieldRecord [, allselectargs::NamedTuple];
    coords=nothing,
    lookup_coords=true,
    add_attributes=true,
    update_name=true,
    omit_recorddim_if_constant=false, 
) -> fa_out::FieldArray

[deprecated] get_array(fr::FieldRecord [; kwargs...] [; allselectargs...]) -> fa_out::FieldArray
```

Return a [`FieldArray`](@ref) containing an Array of values and any attached coordinates, for records and spatial region defined by `allselectargs`.

Combines [`FieldArray(fr::FieldRecord)`](@ref) and [`select(fa::FieldArray)`](@ref)

Optional `allselectargs` field `expand_cartesian` (default `false`) is only needed for spatially resolved output using a `CartesianLinearGrid`,  set to `true` to expand compressed internal data (with spatial dimension `cells`) to a cartesian array  (with spatial dimensions eg `lon`, `lat`, `zt`)

# Keyword arguments

See  [`FieldArray(fr::FieldRecord)`](@ref) and [`select(fa::FieldArray)`](@ref)

# Examples

  * select a timeseries for single cell index 3 :

    ```
    get_array(fr, (cell=3, ))
    ```
  * select first column at nearest available time to model time 10.0 :

    ```
    get_array(fr, (column=1, tmodel=10.0))
    ```
  * set first column at nearest available time to model time 10.0, replacing atmosphere model pressure coordinate with z coordinate:

    ```
    get_array(
        fr, (column=1, tmodel=10.0);
        coords=["cells"=>("atm.zmid", "atm.zlower", "atm.zupper")]
    )
    ```
  * select surface 2D array (dimension `zt`, index 1) from 3D output at nearest available    time to model time 10.0, expanding `CartesianLinearGrid`:

    ```
    get_array(fr, (zt_isel=1, tmodel=10.0, expand_cartesian=true))
    ```
  * select section 2D array at nearest index to longitude 200 degrees from 3D output at nearest available  time to model time 10.0, expanding `CartesianLinearGrid`:

    ```
    get_array(fr, (lon=200.0, tmodel=10.0, expand_cartesian=true))
    ```
  * get full data cube as used for netcdf output, omitting coordinates and attributes, retaining singleton dimensions, and omitting  record dimension if variable is a constant:

    ```
    get_array(
        fr, (expand_cartesian=true, squeeze_all_single_dims=false);
        lookup_coordinates=false, add_attributes=false, omit_recorddim_if_constant=true
    )
    ```

# Limitations

  * it is only possible to select either a single slice or a contiguous range for each dimension, not a set of slices for a Vector of index or coordinate values.
