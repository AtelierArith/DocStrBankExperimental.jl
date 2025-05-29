```
Sat(db::AbstractDatabase; dist::SemiMetric=L2Distance(), root=1)
```

Prepares the metric data structure. After calling this constructor, please call `index!`.

# Arguments

  * `db`: database to index

# Keyword arguments

  * `dist`: distance function, defaults to L2Distance()
  * `root`: The dataset's element to be used as root
