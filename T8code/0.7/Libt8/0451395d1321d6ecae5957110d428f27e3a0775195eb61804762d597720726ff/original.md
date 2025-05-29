```
t8_forest_set_user_function(forest, _function)
```

Set the user function pointer of a forest. This can i.e. be used to pass user defined functions to the adapt routine.

!!! note
    *function* can be an arbitrary function with return value and parameters of your choice. When accessing it with t8*forest*get*user*function you should cast it into the proper type.


# Arguments

  * `forest`:[in,out] The forest
  * `function`:[in] A pointer to a user defined function. t8code will never touch the function. The forest does not need be committed before calling this function.

# See also

[`t8_forest_get_user_function`](@ref)

### Prototype

```c
void t8_forest_set_user_function (t8_forest_t forest, t8_generic_function_pointer function);
```
