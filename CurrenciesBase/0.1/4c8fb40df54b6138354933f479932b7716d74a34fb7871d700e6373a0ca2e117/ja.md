```
iso4217alpha(s::Symbol)   → String
iso4217alpha(m::Monetary) → String
iso4217alpha(t::DataType) → String
```

通貨のISO 4217アルファベットコードを取得します。カスタム通貨の場合、小文字の文字列が返され、これはISO 4217コードとして解釈されるべきではありません。それ以外の場合、3文字の大文字の文字列が返されます。この関数は、シンボル、`Monetary`型、または`Monetary`オブジェクトのいずれかで呼び出すことができます。
