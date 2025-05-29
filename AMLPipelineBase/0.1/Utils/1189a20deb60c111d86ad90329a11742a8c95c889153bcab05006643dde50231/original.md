```
nested_dict_merge(first::Dict, second::Dict)
```

Second nested dictionary is merged into first.

If a second dictionary's value as well as the first are both dictionaries, then a merge is conducted between the two inner dictionaries. Otherwise the second's value overrides the first.

  * `first`: first nested dictionary
  * `second`: second nested dictionary

Returns: merged nested dictionary
