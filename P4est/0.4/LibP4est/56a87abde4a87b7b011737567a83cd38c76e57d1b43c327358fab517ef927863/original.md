```
p4est_connectivity_new_cubed()
```

Create a connectivity structure for the six sides of a unit cube. The ordering of the trees is as follows: 0 1 2 3 <– 3: axis-aligned top side 4 5. This choice has been made for maximum symmetry (see tree_to_* in .c file).

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_new_cubed (void);
```
