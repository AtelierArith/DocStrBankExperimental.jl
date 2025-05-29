```
t8_get_package_id()
```

Query the package identity as registered in libsc.

# Returns

This is -1 before t8_init has been called and a proper package identifier afterwards.

### Prototype

```c
int t8_get_package_id (void);
```
