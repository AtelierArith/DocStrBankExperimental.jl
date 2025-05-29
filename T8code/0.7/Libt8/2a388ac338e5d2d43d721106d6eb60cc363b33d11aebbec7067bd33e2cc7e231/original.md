```
t8_forest_set_copy(forest, from)
```

Set a forest as source for copying on committing. By default, the forest takes ownership of the source **from** such that it will be destroyed on calling t8*forest*commit. To keep ownership of **from**, call t8*forest*ref before passing it into this function. This means that it is ILLEGAL to continue using **from** or dereferencing it UNLESS it is referenced directly before passing it into this function.

!!! note
    This setting cannot be combined with t8*forest*set*adapt, t8*forest*set*partition, or t8*forest*set_balance and overwrites these settings.


# Arguments

  * `forest`:[in,out] The forest.
  * `from`:[in] A second forest from which *forest* will be copied in t8*forest*commit.

### Prototype

```c
void t8_forest_set_copy (t8_forest_t forest, const t8_forest_t from);
```
