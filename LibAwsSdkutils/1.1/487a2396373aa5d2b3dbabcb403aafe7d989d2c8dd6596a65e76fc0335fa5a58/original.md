```
aws_profile_property_get_sub_property(property, sub_property_name)
```

Returns a reference to the value of a sub property with the given name, if it exists, in the property

### Prototype

```c
const struct aws_string *aws_profile_property_get_sub_property( const struct aws_profile_property *property, const struct aws_string *sub_property_name);
```
