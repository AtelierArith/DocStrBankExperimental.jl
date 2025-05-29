```
mice(
    mids::Mids;
    iter::Int = 10,
    progressReports::Bool = true,
    kwargs...
    )
```

既存の `Mids` オブジェクトに追加の反復を加えます。

*追加の* 反復の数は `iter` で指定されます。

`progressReports` も指定できます：他のすべての引数は無視されるか、内部関数に渡されます。
