```
erroruser(msg, exitcode=99)
EnduserError(msg, exitcode=99)
```

The function `erroruser`, similarly to `Base.error`, throws the `EnduserError` exception. This exception is meant to signal obvious errors to *end users*, for example "file 'foo' not found" or "invalid command line option '–foo'". No backtrace is output; if you catch this exception, you should also suppress it.
