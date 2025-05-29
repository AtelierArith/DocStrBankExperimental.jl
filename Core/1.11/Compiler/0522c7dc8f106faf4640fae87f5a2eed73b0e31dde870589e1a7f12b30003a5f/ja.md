```
method_table(interp::AbstractInterpreter) -> MethodTableView
```

この `interp` がメソッドルックアップに使用するメソッドテーブルを返します。外部の `AbstractInterpreter` は、オーバーライドされたメソッドのカスタマイズされたディスパッチを組み込むために、ここでオプションで `OverlayMethodTable` を返すことができます。
