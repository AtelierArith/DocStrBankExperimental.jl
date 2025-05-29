```
debug(sess::PyObject, o::PyObject)
```

In the case a session run yields an error from the TensorFlow backend, this function can help print the exact error.  For example, you might encounter  `InvalidArgumentError()` with no detailed error information, and this function can be useful for debugging.
