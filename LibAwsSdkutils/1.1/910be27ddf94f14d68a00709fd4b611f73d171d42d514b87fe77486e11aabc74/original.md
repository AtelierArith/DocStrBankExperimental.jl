```
aws_profile_collection_new_from_merge(allocator, config_profiles, credentials_profiles)
```

Create a new profile collection by merging a config-file-based profile collection and a credentials-file-based profile collection

### Prototype

```c
struct aws_profile_collection *aws_profile_collection_new_from_merge( struct aws_allocator *allocator, const struct aws_profile_collection *config_profiles, const struct aws_profile_collection *credentials_profiles);
```
