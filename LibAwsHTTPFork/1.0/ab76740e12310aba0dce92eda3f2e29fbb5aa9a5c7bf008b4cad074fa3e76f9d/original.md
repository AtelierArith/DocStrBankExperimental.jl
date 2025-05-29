```
aws_http_header_compression
```

Controls whether a header's strings may be compressed by encoding the index of strings in a cache, rather than encoding the literal string.

This setting has no effect on HTTP/1.x connections. On HTTP/2 connections this controls HPACK behavior. See RFC-7541 Section 7.1 for security considerations.
