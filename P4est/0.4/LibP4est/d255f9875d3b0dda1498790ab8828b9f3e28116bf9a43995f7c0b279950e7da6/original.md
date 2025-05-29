```
sc_version()
```

Return the full version of libsc.

### Returns

Return the version of libsc using the format `VERSION\_MAJOR.VERSION\_MINOR.VERSION\_POINT`, where `VERSION_POINT` can contain dots and characters, e.g. to indicate the additional number of commits and a git commit hash.

### Prototype

```c
const char *sc_version (void);
```
