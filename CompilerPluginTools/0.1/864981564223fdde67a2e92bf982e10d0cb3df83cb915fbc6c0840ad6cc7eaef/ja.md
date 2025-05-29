```
code_ircode([pass, ]f, types; world=get_world_counter(), interp=NativeInterpreter(world))
```

与えられた関数 `f` とその引数の型 `types` によって `IRCode` を取得します。オプション引数 `pass` は、型推論中に IRCode に対する変換関数として指定できます。
