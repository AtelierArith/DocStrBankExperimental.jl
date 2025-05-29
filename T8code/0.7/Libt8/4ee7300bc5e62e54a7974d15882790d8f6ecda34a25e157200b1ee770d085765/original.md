```
t8_forest_init(pforest)
```

Create a new forest with reference count one. This forest needs to be specialized with the t8_forest_set_* calls. Currently it is manatory to either call the functions t8*forest*set*mpicomm, t8*forest*set*cmesh, and t8*forest*set*scheme, or to call one of t8*forest*set*copy, t8*forest*set*adapt, or t8*forest*set*partition. It is illegal to mix these calls, or to call more than one of the three latter functions Then it needs to be set up with t8*forest*commit.

# Arguments

  * `pforest`:[in,out] On input, this pointer must be non-NULL. On return, this pointer set to the new forest.

### Prototype

```c
void t8_forest_init (t8_forest_t *pforest);
```
