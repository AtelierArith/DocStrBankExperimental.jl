The data specification TOML format constructs a DataCollection, which itself contains DataSets, comprised of metadata and AbstractDataTransformers.

```
DataCollection
├─ DataSet
│  ├─ AbstractDataTransformer
│  └─ AbstractDataTransformer
├─ DataSet
⋮
```

Within each scope, there are certain reserved attributes. They are listed in this Dict under the following keys:

  * `:collection` for `DataCollection`
  * `:dataset` for `DataSet`
  * `:transformer` for `AbstractDataTransformer`
