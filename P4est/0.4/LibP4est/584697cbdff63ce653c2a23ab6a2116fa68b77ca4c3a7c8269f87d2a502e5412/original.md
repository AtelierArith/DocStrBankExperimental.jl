```
sc_fwrite(ptr, size, nmemb, file, errmsg)
```

Write memory content to a file.

!!! note
    This function aborts on file errors.


### Parameters

  * `ptr`:[in] Data array to write to disk.
  * `size`:[in] Size of one array member.
  * `nmemb`:[in] Number of array members.
  * `file`:[in,out] File pointer, must be opened for writing.
  * `errmsg`:[in] Error message passed to `SC_CHECK_ABORT`.

### Prototype

```c
void sc_fwrite (const void *ptr, size_t size, size_t nmemb, FILE * file, const char *errmsg);
```
