```
Replace(f, with)
Replace(f; with)
```

このポストプロセッサは、`f(value) === true` であるすべてのセル値を `with` の値に置き換えます。もし `with <: Function` であれば、新しい値は `with(value)` になります。

## 例

```
Replace(x -> x isa String, "A string was here")
Replace(x -> x isa String, uppercase)
Replace(x -> x isa Int && iseven(x), "An even Int was here")
```
