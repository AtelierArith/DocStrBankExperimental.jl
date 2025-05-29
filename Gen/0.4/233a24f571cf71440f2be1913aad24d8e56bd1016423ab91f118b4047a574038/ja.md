```
DynamicDSLFunction{T} <: GenerativeFunction{T,DynamicDSLTrace}
```

Julia関数に基づいた浅い埋め込みモデリング言語に基づく生成関数。

`@gen`キーワードを使用して構築されます。生成関数インターフェースのほとんどのメソッドは、関数のエンドツーエンド実行を含みます。
