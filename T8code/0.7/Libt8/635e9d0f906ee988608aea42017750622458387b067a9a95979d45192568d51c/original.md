```
t8_eclass_compare(eclass1, eclass2)
```

Compare two eclasses of the same dimension as necessary for face neighbor orientation. The implemented order is Triangle < Square in 2D and Tet < Hex < Prism < Pyramid in 3D.

# Arguments

  * `eclass1`:[in] The first eclass to compare.
  * `eclass2`:[in] The second eclass to compare.

# Returns

0 if the eclasses are equal, 1 if eclass1 > eclass2 and -1 if eclass1 < eclass2

### Prototype

```c
int t8_eclass_compare (t8_eclass_t eclass1, t8_eclass_t eclass2);
```
