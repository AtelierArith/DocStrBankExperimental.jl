```
struct StorOpexVar <: AbstractStorageParameters
```

可変運用費用を含むストレージパラメータタイプです。これは、充電または放電率に容量がないことを意味し、[`Storage`](@ref) レベルは単一の `TimePeriod` 内で使用できます。

このタイプは、フィールド `charge` と `discharge` にのみ使用できます。

# フィールド

  * **`opex_var::TimeProfile`** は、可変 `:cap_use` を通じての容量使用あたりの可変運用費用です。
