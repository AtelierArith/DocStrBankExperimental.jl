```
populate_tree!(tree::FelNode, starting_message, names, data; init_all_messages = true, tolerate_missing = 1, leaf_name_transform = x -> x)
```

Takes a tree, and a `starting_message` (which will serve as the memory template for populating messages all over the tree). `starting_message` can be a message (ie. a vector of Partitions), but will also work with a single Partition (although the tree) will still be populated with a length-1 vector of Partitions. Further, as long as `obs2partition` is implemented for your Partition type, the leaf nodes will be populated with the data from `data`, matching the names on each leaf. When a leaf on the tree has a name that doesn't match anything in `names`, then if

  * `tolerate_missing = 0`, an error will be thrown
  * `tolerate_missing = 1`, a warning will be thrown, and the message will be set to the uninformative message (requires identity!(::Partition) to be defined)
  * `tolerate_missing = 2`, the message will be set to the uninformative message, without warnings (requires identity!(::Partition) to be defined)

A renaming function that can eg. strip tags from the tree when matching leaf names with `names` can be passed to `leaf_name_transform`
