```
load(loader::DataLoader{driver}, source::Any, as::Type)
```

Using a certain `loader`, obtain information in the form of `as` from the data given by `source`.

This fulfils this component of the overall data flow:

```
  ╭────loader─────╮
  ╵               ▼
Data          Information
```

When the loader produces `nothing` this is taken to indicate that it was unable to load the data for some reason, and that another loader should be tried if possible. This can be considered a soft failure. Any other value is considered valid information.
