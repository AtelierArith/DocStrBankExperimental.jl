diff = deepdiff(obj1, obj2)

deepdiff computes the structural difference between two objects and returns a diff representing "edits" needed to transform obj1 into obj2. This diff supports the `added`, `removed`, and `modified` functions that return `Set`s of dictionary keys or array indices.
