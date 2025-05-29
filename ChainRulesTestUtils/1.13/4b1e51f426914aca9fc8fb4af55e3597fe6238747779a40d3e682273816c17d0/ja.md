```
test_method_tables()
```

`rrule` と `frule` のメソッドテーブルが妥当であることを確認します。将来的にはいくつかのチェックを行うかもしれませんが、現在は、コンストラクタのルールを書く際に誤って非常に一般的な `DataType`、`Union`、または `UnionAll` タイプにルールが追加されていないことを確認するだけです。例えば、`rrule(::typeof(Foo), x)` と書くのではなく、`rrule(::Type{<:Foo}, x)` と書くと、実際には `rrule(::DataType, x)` が定義されてしまいます。（もし `Foo` がパラメトリックであれば `UnionAll`、`Foo` が `Union` の型エイリアスであれば `Union` になります）
