```
t8_forest_get_user_data(forest)
```

Return the user data pointer associated with a forest.

# Arguments

  * `forest`:[in] The forest.

# Returns

The user data pointer of *forest*. The forest does not need be committed before calling this function.

# See also

[`t8_forest_set_user_data`](@ref)

### Prototype

```c
void * t8_forest_get_user_data (const t8_forest_t forest);
```
