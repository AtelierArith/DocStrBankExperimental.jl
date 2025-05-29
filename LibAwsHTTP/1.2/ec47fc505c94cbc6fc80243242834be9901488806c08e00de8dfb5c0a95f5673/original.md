```
aws_http_header_name_eq(name_a, name_b)
```

Return whether both names are equivalent. This is a case-insensitive string comparison.

Example Matches: "Content-Length" == "content-length" // upper or lower case ok

Example Mismatches: "Content-Length" != " Content-Length" // leading whitespace bad

### Prototype

```c
bool aws_http_header_name_eq(struct aws_byte_cursor name_a, struct aws_byte_cursor name_b);
```
