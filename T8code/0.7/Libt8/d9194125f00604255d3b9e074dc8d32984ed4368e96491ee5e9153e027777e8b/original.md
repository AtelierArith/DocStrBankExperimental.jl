```
t8_forest_get_eclass_scheme(forest, eclass)
```

Return the eclass scheme of a given element class associated to a forest.

!!! note
    The forest is not required to have trees of class *eclass*.


# Arguments

  * `forest.`:[in] A committed forest.
  * `eclass.`:[in] An element class.

# Returns

The eclass scheme of *eclass* associated to forest.

# See also

[`t8_forest_set_scheme`](@ref)

### Prototype

```c
t8_eclass_scheme_c * t8_forest_get_eclass_scheme (t8_forest_t forest, t8_eclass_t eclass);
```
