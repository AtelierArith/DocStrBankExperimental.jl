```
t8_forest_get_user_function(forest)
```

Return the user function pointer associated with a forest.

# Arguments

  * `forest`:[in] The forest.

# Returns

The user function pointer of *forest*. The forest does not need be committed before calling this function.

# See also

[`t8_forest_set_user_function`](@ref)

### Prototype

```c
t8_generic_function_pointer t8_forest_get_user_function (const t8_forest_t forest);
```
