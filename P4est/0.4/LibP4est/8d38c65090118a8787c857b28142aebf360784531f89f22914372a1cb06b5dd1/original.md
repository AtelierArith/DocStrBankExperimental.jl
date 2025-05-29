```
p4est_connectivity_new_byname(name)
```

Create connectivity structure from predefined catalogue.

### Parameters

  * `name`:[in] Invokes connectivity_new_* function. brick23 brick (2, 3, 0, 0) corner corner cubed cubed disk disk moebius moebius periodic periodic pillow pillow rotwrap rotwrap star star unit unitsquare

### Returns

An initialized connectivity if name is defined, NULL else.

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_new_byname (const char *name);
```
