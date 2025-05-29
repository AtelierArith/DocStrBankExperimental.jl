```
p8est_connectivity_deflate(conn, code)
```

Allocate memory and store the connectivity information there.

### Parameters

  * `conn`:[in] The connectivity structure to be exported to memory.
  * `code`:[in] Encoding and compression method for serialization.

### Returns

Newly created array that contains the information.

### Prototype

```c
sc_array_t *p8est_connectivity_deflate (p8est_connectivity_t * conn, p8est_connectivity_encode_t code);
```
