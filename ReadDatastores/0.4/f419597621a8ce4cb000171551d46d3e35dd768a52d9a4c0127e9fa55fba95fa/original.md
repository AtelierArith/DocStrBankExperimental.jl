```
@openreads filename::String
```

A convenience macro for opening read datastores.

The open method for ReadDatastores requires the specific type of the ReadDatastore as the first argument.

This can be cumbersome as the specific type of the datastore may be forgotten or not known in the first place if the user recieved the datastore from a colleague.

This macro allows you to open a datastore using only the filename.

The macro opens the file, peeks at the header and deduces the type of datastore contained in the file. It then returns a complete and correctly formed `open` command for the datastore. This allows the user to forget about the specific datastore type whilst still maintaining type certainty.
