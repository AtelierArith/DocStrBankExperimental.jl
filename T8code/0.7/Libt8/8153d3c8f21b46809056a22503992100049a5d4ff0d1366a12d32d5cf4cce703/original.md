```
t8_tree
```

The t8 tree datatype

| Field           | Note                                                              |
|:--------------- |:----------------------------------------------------------------- |
| elements        | locally stored elements                                           |
| eclass          | The element class of this tree                                    |
| first_desc      | first local descendant                                            |
| last_desc       | last local descendant                                             |
| elements_offset | cumulative sum over earlier trees on this processor (locals only) |
