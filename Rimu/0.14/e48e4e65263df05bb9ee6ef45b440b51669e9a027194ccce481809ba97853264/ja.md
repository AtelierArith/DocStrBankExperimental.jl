```
smart_logger(args...)
```

インタラクティブな使用中にターミナルのプログレスバーを有効にします（すなわち、CIやHPCで実行していない限り）。引数はロガーに渡されます。これは`Rimu`の起動時に一度実行されます。[`default_logger`](@ref)を使用するか、`Base.global_logger()`を設定することで元に戻すことができます。
