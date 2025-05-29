```
HierarchicalLogger(root_logger; [propagate] [, delimiter] [, min_logging_level])
```

Constructs a `HierarchicalLogger` with `root_logger` at its root.

# Arguments

  * `root_logger::AbstractLogger`: Logger associated with the root node
  * `propagate::PropagateToChildren.Mode=PropagateToChildren.None`: Determines how messages send to a node are propagated to its children
  * `delimiter::Char='.'`: Parent-child delimiter in the string representation of a node
  * `min_logging_level::LogLevel=All`: Sets the initial minimum logging level for all loggers
