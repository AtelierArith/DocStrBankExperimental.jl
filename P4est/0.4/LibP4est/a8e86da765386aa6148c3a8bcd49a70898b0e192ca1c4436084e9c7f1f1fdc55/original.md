```
p4est_connectivity_sink(conn, sink)
```

Write connectivity to a sink object.

### Parameters

  * `conn`:[in] The connectivity to be written.
  * `sink`:[in,out] The connectivity is written into this sink.

### Returns

0 on success, nonzero on error.

### Prototype

```c
int p4est_connectivity_sink (p4est_connectivity_t * conn, sc_io_sink_t * sink);
```
