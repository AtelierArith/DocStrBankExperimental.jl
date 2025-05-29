```
aws_compression_library_clean_up()
```

Clean up internal datastructures used by aws-c-compression. Must not be called until application is done using functionality in aws-c-compression.

### Prototype

```c
void aws_compression_library_clean_up(void);
```
