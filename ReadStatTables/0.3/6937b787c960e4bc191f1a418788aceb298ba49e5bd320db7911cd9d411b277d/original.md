```
getvaluelabels(tb::ReadStatTable)
getvaluelabels(tb::ReadStatTable, name::Symbol)
```

Return a dictionary of all value label dictionaries contained in `tb` obtained from the data file. Return a specific dictionary of value labels if a `name` is specified.

Each dictionary of value labels is associated with a name that may appear in the variable-level metadata under the key `vallabel` for identifying the dictionary of value labels attached to each data column. The same dictionary may be associated with multiple data columns. Modifying the metadata value of `vallabel` for a data column switches the associated value labels for the data column. If the metadata value is set to `Symbol("")`, the data column is not associated with any value label.
