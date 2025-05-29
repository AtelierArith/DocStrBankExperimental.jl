```
sc_io_error_t
```

Error values for io.

| Enumerator        | Note                                                                        |
|:----------------- |:--------------------------------------------------------------------------- |
| SC_IO_ERROR_NONE  | The value of zero means no error.                                           |
| SC_IO_ERROR_FATAL | The io object is now disfunctional.                                         |
| SC_IO_ERROR_AGAIN | Another io operation may resolve it. The function just returned was a noop. |
