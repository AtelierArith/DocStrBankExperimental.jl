```
flatten(g::SchematicGraph; depth=-1)
```

Create a copy of `g` with all `AbstractCompositeComponent`s replaced by their graphs.

For non-composite components, the identical `ComponentNode`s will be preserved.

# Keywords

  * `depth`: How many times to iteratively flatten top-level `AbstractCompositeComponent`s. If negative, will repeat until no `AbstractCompositeComponent`s remain.
