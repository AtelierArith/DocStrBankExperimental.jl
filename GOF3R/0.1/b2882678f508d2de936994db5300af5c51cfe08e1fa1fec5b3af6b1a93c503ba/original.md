```
s3stream(f, bucket, path)
```

Call `f(s3stream(bucket, path))`, ensuring that the stream is closed properly once `f` has finished executing, including in the case of errors.
