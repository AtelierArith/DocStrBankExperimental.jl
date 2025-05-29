```
arg_grads = gradient(gen_fn::CustomDetermGF, args, retval, retgrad)
```

引数に関して勾配タプルを返します。ここで、`nothing`は勾配が利用できない引数に対して使用されます。
