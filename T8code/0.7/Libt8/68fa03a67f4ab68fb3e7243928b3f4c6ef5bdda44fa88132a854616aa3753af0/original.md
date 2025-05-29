```
t8_cmesh_init(pcmesh)
```

Create a new cmesh with reference count one. This cmesh needs to be specialized with the t8_cmesh_set_* calls. Then it needs to be set up with t8*cmesh*commit.

# Arguments

  * `pcmesh`:[in,out] On input, this pointer must be non-NULL. On return, this pointer set to the new cmesh.

### Prototype

```c
void t8_cmesh_init (t8_cmesh_t *pcmesh);
```
