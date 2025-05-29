```
Crediting(d::OrderedDict) -> crediting
```

Constructs a Crediting structure from `d`, an OrderedDict read in from the config file inside of a mod.  The Crediting structure is of type `d[:type]` with keyword arguments for all the other key value pairs in `d`.
