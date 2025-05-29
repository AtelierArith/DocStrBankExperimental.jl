```
aws_profile_get_property(profile, property_name)
```

Retrieves a reference to a property with the specified name, if it exists, from a profile

### Prototype

```c
const struct aws_profile_property *aws_profile_get_property( const struct aws_profile *profile, const struct aws_string *property_name);
```
