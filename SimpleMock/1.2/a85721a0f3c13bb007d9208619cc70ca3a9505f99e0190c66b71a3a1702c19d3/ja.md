```
Predicate(f)
```

リテラル呼び出し引数の代わりに使用できる述語で、引数の正確な値がわからない状況で便利です。関数 `f` は観測された引数で呼び出され、`Bool` を返さなければなりません。

## 例

```julia
m = Mock()
m(rand(1:10))
@assert called_with(m, Predicate(in(1:10)))
```
