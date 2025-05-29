```
t8_forest_set_adapt(forest, set_from, adapt_fn, recursive)
```

Set a source forest with an adapt function to be adapted on committing. By default, the forest takes ownership of the source **set_from** such that it will be destroyed on calling t8*forest*commit. To keep ownership of **set_from**, call t8*forest*ref before passing it into this function. This means that it is ILLEGAL to continue using **set_from** or dereferencing it UNLESS it is referenced directly before passing it into this function.

!!! note
    This setting can be combined with t8*forest*set*partition and t8*forest*set*balance. The order in which these operations are executed is always 1) Adapt 2) Balance 3) Partition


!!! note
    This setting may not be combined with t8*forest*set_copy and overwrites this setting.


# Arguments

  * `forest`:[in,out] The forest
  * `set_from`:[in] The source forest from which **forest** will be adapted. We take ownership. This can be prevented by referencing **set_from**. If NULL, a previously (or later) set forest will be taken (t8*forest*set*partition, t8*forest*set*balance).
  * `adapt_fn`:[in] The adapt function used on committing.
  * `recursive`:[in] A flag specifying whether adaptation is to be done recursively or not. If the value is zero, adaptation is not recursive and it is recursive otherwise.

### Prototype

```c
void t8_forest_set_adapt (t8_forest_t forest, const t8_forest_t set_from, t8_forest_adapt_t adapt_fn, int recursive);
```
