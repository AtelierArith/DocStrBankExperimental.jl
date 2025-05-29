```
p8est_connectivity_new_byname(name)
```

Create connectivity structure from predefined catalogue.

### Parameters

  * `name`:[in] Invokes connectivity_new_* function. brick235 brick (2, 3, 5, 0, 0, 0) periodic periodic rotcubes rotcubes rotwrap rotwrap shell shell sphere sphere twocubes twocubes twowrap twowrap unit unitcube

### Returns

An initialized connectivity if name is defined, NULL else.

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_new_byname (const char *name);
```
