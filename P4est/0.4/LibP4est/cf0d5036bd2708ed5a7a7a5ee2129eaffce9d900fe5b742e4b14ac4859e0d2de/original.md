```
sc_array_reset(array)
```

Sets the array count to zero and frees all elements. This function turns a view into a newly initialized array.

!!! note
    Calling [`sc_array_init`](@ref), then any array operations, then [`sc_array_reset`](@ref) is memory neutral. As an exception, the two functions [`sc_array_init_view`](@ref) and [`sc_array_init_data`](@ref) do not require a subsequent call to [`sc_array_reset`](@ref). Regardless, it is legal to call [`sc_array_reset`](@ref) anyway.


### Parameters

  * `array`:[in,out] Array structure to be reset.

### Prototype

```c
void sc_array_reset (sc_array_t * array);
```
