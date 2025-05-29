```
t8_cmesh_destroy(pcmesh)
```

Verify that a coarse mesh has only one reference left and destroy it. This function is preferred over t8*cmesh*unref when it is known that the last reference is to be deleted.

# Arguments

  * `pcmesh`:[in,out] This cmesh must have a reference count of one. It can be in any state (committed or not). Then it effectively calls t8*cmesh*unref.
  * `comm`:[in] A mpi communicator that is valid with *cmesh*.

### Prototype

```c
void t8_cmesh_destroy (t8_cmesh_t *pcmesh);
```
