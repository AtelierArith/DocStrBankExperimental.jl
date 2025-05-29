```
@use "filename.dta", [clear]
```

Read the data from the file `filename.dta` and set it as the global data frame. If there is already a global data frame, `@use` will throw an error unless the `clear` option is provided
