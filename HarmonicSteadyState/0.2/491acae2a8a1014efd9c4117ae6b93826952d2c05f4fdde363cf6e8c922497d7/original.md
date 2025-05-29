```
get_solutions(
    res::Result, x::String;
    branches=1:branch_count(res), realify=false, class=["stable"], not_class=[]
    )
get_solutions(res::Result; branches=1:branch_count(res), class=["stable"], not_class=[])
```

Extract solution vectors from a `Result` object based on specified filtering criteria given by the `class` keywords. The first method allows extracting a specific solution component by name `x`. The second method returns complete solution vectors.

# Keyword arguments

  * `branches=1:branch_count(res)`: Range of branches to include in the output
  * `realify=false`: Whether to convert complex solutions to real form
  * `class=["physical", "stable"]`: Array of classification labels to include
  * `not_class=[]`: Array of classification labels to exclude

# Returns

Filtered solution vectors matching the specified criteria
