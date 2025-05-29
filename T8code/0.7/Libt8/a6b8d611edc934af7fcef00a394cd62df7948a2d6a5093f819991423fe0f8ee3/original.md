```
t8_element_array_t
```

The [`t8_element_array_t`](@ref) is an array to store [`t8_element_t`](@ref) * of a given eclass_scheme implementation. It is a wrapper around sc*array*t. Each time, a new element is created by the functions for t8*element*array*t, the eclass function either t8*element*new or t8*element*init is called for the element. Thus, each element in a t8*element*array*t is automatically initialized properly.

| Field  | Note                                                |
|:------ |:--------------------------------------------------- |
| scheme | An eclass scheme of which elements should be stored |
| array  | The array in which the elements are stored          |
