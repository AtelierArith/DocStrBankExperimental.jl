```
t8_forest_set_balance(forest, set_from, no_repartition)
```

Set a source forest to be balanced during commit. A forest is said to be balanced if each element has face neighbors of level at most +1 or -1 of the element's level.

!!! note
    This setting can be combined with t8*forest*set*adapt and t8*forest*set*balance. The order in which these operations are executed is always 1) Adapt 2) Balance 3) Partition.


!!! note
    This setting may not be combined with t8*forest*set_copy and overwrites this setting.


# Arguments

  * `forest`:[in,out] The forest.
  * `set_from`:[in] A second forest that should be balanced. We take ownership. This can be prevented by referencing **set_from**. If NULL, a previously (or later) set forest will be taken (t8*forest*set*adapt, t8*forest*set*partition)
  * `no_repartition`:[in] Balance constructs several intermediate forest that are refined from each other. In order to maintain a balanced load these forest are repartitioned in each round and the resulting forest is load-balanced per default. If this behaviour is not desired, *no_repartition* should be set to true. If *no_repartition* is false, an additional call of t8*forest*set_partition is not necessary.

### Prototype

```c
void t8_forest_set_balance (t8_forest_t forest, const t8_forest_t set_from, int no_repartition);
```
