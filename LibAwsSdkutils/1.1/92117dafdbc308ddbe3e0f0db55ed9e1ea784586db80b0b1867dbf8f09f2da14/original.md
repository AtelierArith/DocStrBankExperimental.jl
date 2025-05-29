```
aws_resource_name_init_from_cur(arn, input)
```

Given an ARN "Amazon Resource Name" represented as an in memory a structure representing the parts

### Prototype

```c
int aws_resource_name_init_from_cur(struct aws_resource_name *arn, const struct aws_byte_cursor *input);
```
