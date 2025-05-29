```
t8_forest_get_maxlevel(forest)
```

Return the maximum allowed refinement level for any element in a forest.

# Arguments

  * `forest`:[in] A forest.

# Returns

The maximum level of refinement that is allowed for an element in this forest. It is guaranteed that any tree in *forest* can be refined this many times and it is not allowed to refine further. *forest* must be committed before calling this function. For forest with a single element class (non-hybrid) maxlevel is the maximum refinement level of this element class, whilst for hybrid forests the maxlevel is the minimum of all maxlevels of the element classes in this forest.

### Prototype

```c
int t8_forest_get_maxlevel (const t8_forest_t forest);
```
