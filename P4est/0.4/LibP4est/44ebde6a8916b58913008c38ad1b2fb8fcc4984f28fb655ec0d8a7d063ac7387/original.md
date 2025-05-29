```
sc_list_append(list, data)
```

Insert a list element at the end of the list.

### Parameters

  * `list`:[in,out] Valid list object.
  * `data`:[in] A new link is created holding this data.

### Returns

The link that has been created for data.

### Prototype

```c
sc_link_t *sc_list_append (sc_list_t * list, void *data);
```
