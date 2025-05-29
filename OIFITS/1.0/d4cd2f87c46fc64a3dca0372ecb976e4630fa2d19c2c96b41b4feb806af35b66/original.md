```
OI_TARGET(lst=OITargetEntry[]; revn=0)
```

yields an `OI_TARGET` data-block. Optional argument `lst` is a vector of `OITargetEntry` specifying the targets (none by default). Keyword `revn` specifies the revision number.

An instance, say `db`, of `OI_TARGET` has the following properties:

```
db.extname # OI-FITS extension name
db.list    # list of targets
db.revn    # revision number
```

and can be used as an iterable or as an array to access the targets individually by their index or by their name:

```
length(db) # the number of targets
db[i]      # the i-th target
db[key]    # the target whose name matches string `key`

for tgt in db; ...; end # loop over all targets
```

Note that, when an `OI_TARGET` instance is pushed in a data-set, target identifiers (field `target_id`) are automatically rewritten to be identical to the index in the list of targets of the data-set.

Standard methods `get` and `haskey` work as expected and according to the type (integer or string) of the key. For the `keys` method, the default is to return an iterator over the target names, but the type of the expected keys can be specified:

```
keys(db)          # iterator over target names
keys(String, db)  # idem
keys(Integer, db) # iterator over target indices
keys(Int, db)     # idem
```

Call [`OIFITS.get_column`](@ref) to retrieve a given target field for all targets of `OI_TARGET` data-block in the form of a vector.
