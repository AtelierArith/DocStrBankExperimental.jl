```
sc_fread(ptr, size, nmemb, file, errmsg)
```

Read file content into memory.

!!! note
    This function aborts on file errors.


### Parameters

  * `ptr`:[out] Data array to read from disk.
  * `size`:[in] Size of one array member.
  * `nmemb`:[in] Number of array members.
  * `file`:[in,out] File pointer, must be opened for reading.
  * `errmsg`:[in] Error message passed to `SC_CHECK_ABORT`.

### Prototype

```c
void sc_fread (void *ptr, size_t size, size_t nmemb, FILE * file, const char *errmsg);
```
