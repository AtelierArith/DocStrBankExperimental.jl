```
aws_http_headers_get_index(headers, index, out_header)
```

Get the header at the specified index. The index of a given header may change any time headers are modified. When iterating headers, the following ordering rules apply:

  * Headers with the same name will always be in the same order, relative to one another. If "A: one" is added before "A: two", then "A: one" will always precede "A: two".
  * Headers with different names could be in any order, relative to one another. If "A: one" is seen before "B: bee" in one iteration, you might see "B: bee" before "A: one" on the next.

AWS_ERROR_INVALID_INDEX is raised if the index is invalid.

### Prototype

```c
int aws_http_headers_get_index( const struct aws_http_headers *headers, size_t index, struct aws_http_header *out_header);
```
