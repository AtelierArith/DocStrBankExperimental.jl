```
struct StorCapOpex <: AbstractStorageParameters
```

容量と変動および固定の運用費用を含むストレージパラメータタイプです。

# フィールド

  * **`capacity::TimeProfile`** は、設置された容量です。
  * **`opex_var::TimeProfile`** は、変動する運用費用で、容量使用量を表す変数 `:cap_use` を通じて示されます。
  * **`opex_fixed::TimeProfile`** は、設置された容量あたりの固定運用費用で、変数 `:cap_inst` を通じて示されます。
