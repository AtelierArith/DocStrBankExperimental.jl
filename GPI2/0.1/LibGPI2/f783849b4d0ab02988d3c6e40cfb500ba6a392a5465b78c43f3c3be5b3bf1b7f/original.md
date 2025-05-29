```
gaspi_group_create(group)
```

Create a group. In case of success, a empty group is created (without members).

### Parameters

  * `group`: The created group.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_group_create (gaspi_group_t * const group);
```
