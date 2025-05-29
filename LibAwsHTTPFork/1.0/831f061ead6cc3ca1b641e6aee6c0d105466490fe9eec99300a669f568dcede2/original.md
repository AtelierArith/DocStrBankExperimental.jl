```
aws_http_library_clean_up()
```

Clean up internal datastructures used by aws-c-http. Must not be called until application is done using functionality in aws-c-http.

### Prototype

```c
void aws_http_library_clean_up(void);
```
