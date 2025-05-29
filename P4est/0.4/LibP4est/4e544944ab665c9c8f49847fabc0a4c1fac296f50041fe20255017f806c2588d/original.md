```
sc_list_insert(list, pred, data)
```

Insert an element after a given list position.

### Parameters

  * `list`:[in,out] Valid list object.
  * `pred`:[in,out] The predecessor of the element to be inserted.
  * `data`:[in] A new link is created holding this data.

### Returns

The link that has been created for data.

### Prototype

```c
sc_link_t *sc_list_insert (sc_list_t * list, sc_link_t * pred, void *data);
```
