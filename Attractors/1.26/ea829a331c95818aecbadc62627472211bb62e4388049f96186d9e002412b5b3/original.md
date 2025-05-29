```
next_free_id(new::Dict, old::Dict)
```

Return the minimum key of the "new" dictionary that doesn't exist in the "old" dictionary. If one of the two dictionaries are empty, return its maximum key + 1. If both are empty, return 1.

The function assumes tha the dictionary keys are integers.
