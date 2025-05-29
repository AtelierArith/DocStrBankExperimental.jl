```
sc_array_checksum(array)
```

Computes the adler32 checksum of array data (see zlib documentation). This is a faster checksum than crc32, and it works with zeros as data.

### Prototype

```c
unsigned int sc_array_checksum (sc_array_t * array);
```
