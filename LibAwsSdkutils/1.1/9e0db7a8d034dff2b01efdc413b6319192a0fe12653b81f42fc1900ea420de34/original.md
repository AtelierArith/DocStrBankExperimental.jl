```
aws_endpoints_rule_engine_new(allocator, ruleset, partitions_config)
```

Create new rule engine for a given ruleset. In cases of failure NULL is returned and last error is set.

### Prototype

```c
struct aws_endpoints_rule_engine *aws_endpoints_rule_engine_new( struct aws_allocator *allocator, struct aws_endpoints_ruleset *ruleset, struct aws_partitions_config *partitions_config);
```
