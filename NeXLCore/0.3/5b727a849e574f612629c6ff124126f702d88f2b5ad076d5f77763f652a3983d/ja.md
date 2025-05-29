```
shell(tr::Transition)
```

遷移の内部シェルに関連付けられたシェル (Shell(1), Shell(2),...) を返します。

例:

```
@assert shell(n"K-L3")==Shell(1)
@assert shell(n"M5-N7")==Shell(3)
```
