```
t8_cmesh_unref(pcmesh)
```

Decrease the reference counter of a cmesh. If the counter reaches zero, this cmesh is destroyed. See also t8*cmesh*destroy, which is to be preferred when it is known that the last reference to a cmesh is deleted.

# Arguments

  * `pcmesh`:[in,out] On input, the cmesh pointed to must exist with positive reference count. It may be in any state. If the reference count reaches zero, the cmesh is destroyed and this pointer set to NULL. Otherwise, the pointer is not changed and the cmesh is not modified in other ways.

### Prototype

```c
void t8_cmesh_unref (t8_cmesh_t *pcmesh);
```
