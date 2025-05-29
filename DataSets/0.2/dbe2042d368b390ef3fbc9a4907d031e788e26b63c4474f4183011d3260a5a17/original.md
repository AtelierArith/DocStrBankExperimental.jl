```
@datarun [proj] func(args...)
```

Run `func` with the named `DataSet`s from the list `args`.

# Example

Load `DataSet`s named a,b as defined in Data.toml, and pass them to `f()`.

```
proj = DataSets.load_project("Data.toml")
@datarun proj f("a", "b")
```
