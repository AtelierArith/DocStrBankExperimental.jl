```
p4est_version()
```

Return the full version of `p4est`.

### Returns

Return the version of `p4est` using the format `VERSION\_MAJOR.VERSION\_MINOR.VERSION\_POINT`, where `VERSION_POINT` can contain dots and characters, e.g. to indicate the additional number of commits and a git commit hash.

### Prototype

```c
const char *p4est_version (void);
```
