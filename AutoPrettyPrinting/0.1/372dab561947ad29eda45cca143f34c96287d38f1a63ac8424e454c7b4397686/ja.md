```
PPrintContext(io::IO, [mime::MIME])
```

与えられたストリームをラップする `PPrintContext` を作成します。

その後の `Base.show(context::PPrintContext, ::MIME, x)` への呼び出しは、このパッケージで提供される美しい印刷機構を使用して `x` をレンダリングします。この型は主に `x` に `custom_tile` メソッドが定義されている（またはこのパッケージによって提供されている）場合に便利ですが、主要な `Base.show` メソッドはこのパッケージの外で定義されており、オーバーライドすべきではありません。

さらに、`mime::MIME` 型が提供されると、`Base.show(context::PPrintContext, x)` へのその後の呼び出しは、提供された `mime` インスタンスを使用してディスパッチされます。
