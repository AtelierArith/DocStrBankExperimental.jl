```
aws_s3_meta_request_options
```

Options for a new meta request, ie, file transfer that will be handled by the high performance client.

There are several ways to pass the request's body data: 1) If the data is already in memory, set the body-stream on `message`. 2) If the data is on disk, set `send_filepath` for best performance. 3) If the data is available, but copying each chunk is asynchronous, set `send_async_stream`. 4) If you're not sure when each chunk of data will be available, use `send_using_async_writes`.
