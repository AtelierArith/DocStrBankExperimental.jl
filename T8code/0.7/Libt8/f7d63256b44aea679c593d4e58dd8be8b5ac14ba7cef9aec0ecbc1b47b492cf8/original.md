```
t8_forest_commit(forest)
```

After allocating and adding properties to a forest, commit the changes. This call sets up the internal state of the forest.

# Arguments

  * `forest`:[in,out] Must be created with t8*forest*init and specialized with t8_forest_set_* calls first.

### Prototype

```c
void t8_forest_commit (t8_forest_t forest);
```
