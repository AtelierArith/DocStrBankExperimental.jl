```
swapfield!(value, name::Symbol, x, [order::Symbol])
swapfield!(value, i::Int, x, [order::Symbol])
```

これらは、フィールドを同時に取得して設定する操作を原子的に実行します：

```
y = getfield(value, name)
setfield!(value, name, x)
return y
```
