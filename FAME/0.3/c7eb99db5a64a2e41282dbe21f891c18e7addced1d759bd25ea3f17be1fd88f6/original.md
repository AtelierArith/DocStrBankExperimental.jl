```
check_status(status)
```

Check the status code returned by cfmXYZ functions. If status indicates success we do nothing, otherwise we trigger an HLIError with the error code and the message.
