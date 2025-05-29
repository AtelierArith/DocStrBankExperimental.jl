```
deidentify(cfg::ProjectConfig)
```

This is the constructor for the `DeIdentified` struct. We use this type to store arrays of `DeIdDataFrame` variables, while also keeping a common `salt_dict` and `dateshift_dict` between `DeIdDataFrame`s. The `salt_dict` allows us to track what salt was used on what cleartext. This is only necessary in the case of doing re-identification. The `id_dict` argument is a dictionary containing the hash digest of the original primary ID to our new research IDs.
