```
struct StorCapOpexVar <: AbstractStorageParameters
```

容量と変動運営費を含むストレージパラメータタイプです。これは、設置された容量が目的関数に直接的な影響を与えないことを意味します。

# フィールド

  * **`capacity::TimeProfile`** は設置された容量です。
  * **`opex_var::TimeProfile`** は変動運営費で、変数 `:cap_use` を通じて容量使用あたりの費用です。
