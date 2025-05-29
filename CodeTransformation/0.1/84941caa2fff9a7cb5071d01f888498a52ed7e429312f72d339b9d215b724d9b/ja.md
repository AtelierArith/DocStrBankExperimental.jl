```
addmethod!(f, argtypes, ci)
```

関数にメソッドを追加します。

引数の型は `Tuple` として与えられます。

例:

```
g(x) = x + 13
ci = code_lowered(g)[1]
function f end
addmethod!(f, (Any,), ci)
f(1) # 14を返します
```
