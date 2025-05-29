```
load_init(file_name :: String; fast = false)
```

Load initial data from  the file with name `file_name` (and extension ".h5").

Keyword argument `fast` is optional (default is `false`), and corresponds the the keyword argument of the function `Init`.

Return an object of type `InitialData`.
