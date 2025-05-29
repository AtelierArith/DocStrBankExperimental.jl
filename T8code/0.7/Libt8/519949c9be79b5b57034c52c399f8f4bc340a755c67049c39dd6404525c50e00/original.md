```
t8_stash_attribute
```

The attribute information that is stored before a cmesh is committed. The pair (package_id, key) serves as a lookup key to identify the data.

| Field      | Note                                                                   |
|:---------- |:---------------------------------------------------------------------- |
| id         | The global tree id                                                     |
| attr_size  | The size (in bytes) of this attribute                                  |
| attr_data  | Array of *size* bytes storing the attributes data.                     |
| is_owned   | True if the data was copied, false if the data is still owned by user. |
| package_id | The id of the package that set this attribute.                         |
| key        | The key used by the package to identify this attribute.                |
