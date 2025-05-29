```
methranges = rename_framemethods!([interp::Interpreter=RecursiveInterpreter()], frame::Frame)
```

`frame`内のgensymmedメソッドの名前を、現在アクティブなものに一致するように変更します。問題の詳細はhttps://github.com/JuliaLang/julia/issues/30908に記載されています。`frame`は必要に応じてインプレースで変更されます。

メソッド定義が発生する`frame`内の行の範囲を指定する`name=>start:stop`ペアのベクターを返します。場合によっては、同じ`start:stop`範囲内に同じ名前のメソッドが複数存在することがあります。
