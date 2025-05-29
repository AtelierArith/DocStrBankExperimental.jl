```
code_ircode_by_signature([pass, ]sig; world=get_world_counter(), interp=NativeInterpreter(world))
```

与えられたシグネチャによって `IRCode` を取得します。最初の引数を使用して、解釈中に `IRCode` を変換することができます。
