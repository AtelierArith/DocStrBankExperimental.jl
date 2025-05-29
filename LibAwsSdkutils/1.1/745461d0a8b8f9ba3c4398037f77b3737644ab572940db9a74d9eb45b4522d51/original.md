```
aws_profile_collection_get_profile(profile_collection, profile_name)
```

Retrieves a reference to a profile with the specified name, if it exists, from the profile collection

### Prototype

```c
const struct aws_profile *aws_profile_collection_get_profile( const struct aws_profile_collection *profile_collection, const struct aws_string *profile_name);
```
