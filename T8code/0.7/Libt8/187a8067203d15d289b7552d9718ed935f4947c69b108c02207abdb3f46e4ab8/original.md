```
t8_forest_set_user_data(forest, data)
```

Set the user data of a forest. This can i.e. be used to pass user defined arguments to the adapt routine.

# Arguments

  * `forest`:[in,out] The forest
  * `data`:[in] A pointer to user data. t8code will never touch the data. The forest does not need be committed before calling this function.

# See also

[`t8_forest_get_user_data`](@ref)

### Prototype

```c
void t8_forest_set_user_data (t8_forest_t forest, void *data);
```
