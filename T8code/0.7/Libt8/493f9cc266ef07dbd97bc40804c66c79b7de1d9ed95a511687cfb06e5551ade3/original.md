```
t8_forest_unref(pforest)
```

Decrease the reference counter of a forest. If the counter reaches zero, this forest is destroyed. In this case, the forest dereferences its cmesh and scheme members.

# Arguments

  * `pforest`:[in,out] On input, the forest pointed to must exist with positive reference count. It may be in any state. If the reference count reaches zero, the forest is destroyed and this pointer set to NULL. Otherwise, the pointer is not changed and the forest is not modified in other ways.

### Prototype

```c
void t8_forest_unref (t8_forest_t *pforest);
```
