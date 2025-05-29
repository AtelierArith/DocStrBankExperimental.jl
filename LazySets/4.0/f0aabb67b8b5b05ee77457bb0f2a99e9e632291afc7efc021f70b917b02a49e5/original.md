```
vertices_list(em::ExponentialMap; [backend]=get_exponential_backend())
```

Return the list of vertices of a (polytopic) exponential map.

### Input

  * `em`      – polytopic exponential map
  * `backend` – (optional; default: `get_exponential_backend()`) exponentiation              backend

### Output

A list of vertices.

### Algorithm

We assume that the underlying set `X` is polytopic. Then the result is just the exponential map applied to the vertices of `X`.
