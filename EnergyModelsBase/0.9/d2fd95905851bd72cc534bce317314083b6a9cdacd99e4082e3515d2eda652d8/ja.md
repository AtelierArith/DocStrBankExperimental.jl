```
struct StorCapOpexFixed <: AbstractStorageParameters
```

容量と固定運営費を含むストレージパラメータタイプです。これは、設置された容量が目的関数に直接影響を与えないことを意味します。

# フィールド

  * **`capacity::TimeProfile`** は設置された容量です。
  * **`opex_fixed::TimeProfile`** は、変数 `:cap_inst` を通じて設置された容量あたりの固定運営費です。
