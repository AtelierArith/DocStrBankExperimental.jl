```
aws_mqtt_validate_utf8_text(text)
```

Validate utf-8 string under mqtt specs

# Arguments

  * `text`:

# Returns

AWS_OP_SUCCESS if the text is validate, otherwise AWS_OP_ERR

### Prototype

```c
int aws_mqtt_validate_utf8_text(struct aws_byte_cursor text);
```
