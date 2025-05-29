```
t8_cmesh_set_refine(cmesh, level, scheme)
```

Refine the cmesh to a given level. Thus split each tree into x^level subtrees TODO: implement

### Prototype

```c
void t8_cmesh_set_refine (t8_cmesh_t cmesh, int level, t8_scheme_cxx_t *scheme);
```
