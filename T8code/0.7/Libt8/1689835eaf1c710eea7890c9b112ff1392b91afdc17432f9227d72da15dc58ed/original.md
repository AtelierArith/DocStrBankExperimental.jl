```
t8_forest_set_partition(forest, set_from, set_for_coarsening)
```

Set a source forest to be partitioned during commit. The partitioning is done according to the SFC and each rank is assigned the same (maybe +1) number of elements.

!!! note
    This setting can be combined with t8*forest*set*adapt and t8*forest*set*balance. The order in which these operations are executed is always 1) Adapt 2) Balance 3) Partition If t8*forest*set*balance is called with the *no*repartition* parameter set as false, it is not necessary to call t8*forest*set_partition additionally.


!!! note
    This setting may not be combined with t8*forest*set_copy and overwrites this setting.


# Arguments

  * `forest`:[in,out] The forest.
  * `set_from`:[in] A second forest that should be partitioned. We take ownership. This can be prevented by referencing **set_from**. If NULL, a previously (or later) set forest will be taken (t8*forest*set*adapt, t8*forest*set*balance).
  * `set_for_coarsening`:[in] CURRENTLY DISABLED. If true, then the partitions are choose such that coarsening an element once is a process local operation.

### Prototype

```c
void t8_forest_set_partition (t8_forest_t forest, const t8_forest_t set_from, int set_for_coarsening);
```
