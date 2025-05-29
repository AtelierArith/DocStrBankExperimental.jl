```
generatehw([io::IO = IOBuffer()], f, args...;
           top = nameof(f), submodules = [],
           transforms = [insertrng!, constantreduction!])
```

`f(args...)`を回路として`top`という名前のSystemVerilogモジュールを生成します。SystemVerilogを生成する前に回路に`transforms`を適用します。
