```
SortedDict()
```

Construct an empty `SortedDict` with key type `Any` and value type `Any`. Ordering defaults to `Forward` ordering.

**Note that a key type of `Any` or any other abstract type will lead to slow performance, as the values are stored boxed (i.e., as pointers), and insertion will require a run-time lookup of the appropriate comparison function. It is recommended to always specify a concrete key type, or to use one of the constructors below in which the key type is inferred.**
