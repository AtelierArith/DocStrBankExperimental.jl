```
aws_pem_objects_init_from_file_contents(pem_objects, alloc, pem_cursor)
```

Decodes PEM data and reads objects sequentially adding them to pem_objects. If it comes across an object it cannot read, list of all object read until that point is returned. If no objects can be read from PEM or objects could not be base 64 decoded, AWS_ERROR_PEM_MALFORMED is raised. out_pem_objects stores [`aws_pem_object`](@ref) struct by value. Function will initialize pem_objects list. This code is slow, and it allocates, so please try not to call this in the middle of something that needs to be fast or resource sensitive.

### Prototype

```c
int aws_pem_objects_init_from_file_contents( struct aws_array_list *pem_objects, struct aws_allocator *alloc, struct aws_byte_cursor pem_cursor);
```
