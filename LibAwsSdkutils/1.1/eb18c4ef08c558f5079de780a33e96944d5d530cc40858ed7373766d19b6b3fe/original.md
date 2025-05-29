```
aws_resource_name_length(arn, size)
```

Calculates the space needed to write an ARN to a byte buf

### Prototype

```c
int aws_resource_name_length(const struct aws_resource_name *arn, size_t *size);
```
