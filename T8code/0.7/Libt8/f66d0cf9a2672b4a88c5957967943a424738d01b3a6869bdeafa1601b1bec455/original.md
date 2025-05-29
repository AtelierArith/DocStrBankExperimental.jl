```
t8_element_new(ts, length, elems)
```

Allocate memory for an array of elements of a given class and initialize them.

!!! note
    Not every element that is created in t8code will be created by a call to this function. However, if an element is not created using t8*element*new, then it is guaranteed that t8*element*init is called on it.


!!! note
    In debugging mode, an element that was created with t8*element*new must pass t8*element*is_valid.


!!! note
    If an element was created by t8*element*new then t8*element*init may not be called for it. Thus, t8*element*new should initialize an element in the same way as a call to t8*element*init would.


# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `length`:[in] The number of elements to be allocated.
  * `elems`:[in,out] On input an array of **length** many unallocated element pointers. On output all these pointers will point to an allocated and initialized element.

# See also

t8_element_init, t8_element_is_valid

### Prototype

```c
void t8_element_new (const t8_eclass_scheme_c *ts, int length, t8_element_t **elems);
```
