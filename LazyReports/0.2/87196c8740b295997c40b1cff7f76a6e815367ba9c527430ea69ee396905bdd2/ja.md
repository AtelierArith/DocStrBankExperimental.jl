```
lazytable(tbl; headers = missing)
```

`tbl`をラップ/変換して`LazyTable`を返します。これは[`lazyreport`](@ref)で使用されます。

`headers`が`missing`の場合、デフォルトのヘッダーは`tbl`の列名から生成されます。`headers`が`AbstractDict`の場合、デフォルトの列名はそれに含まれるキーと値に従って上書きされます。`headers`が`AbstractVector`の場合、テーブルのすべてのヘッダーを明示的に定義し、`tbl`の列数と同じ長さでなければなりません。
