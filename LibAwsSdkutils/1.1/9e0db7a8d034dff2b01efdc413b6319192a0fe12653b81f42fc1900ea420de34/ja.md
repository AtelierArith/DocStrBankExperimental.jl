```
aws_endpoints_rule_engine_new(allocator, ruleset, partitions_config)
```

指定されたルールセットの新しいルールエンジンを作成します。失敗した場合はNULLが返され、最後のエラーが設定されます。

### プロトタイプ

```c
struct aws_endpoints_rule_engine *aws_endpoints_rule_engine_new( struct aws_allocator *allocator, struct aws_endpoints_ruleset *ruleset, struct aws_partitions_config *partitions_config);
```
