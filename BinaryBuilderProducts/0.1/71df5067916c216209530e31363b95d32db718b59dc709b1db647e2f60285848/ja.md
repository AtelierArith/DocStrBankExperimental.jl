```
locate(lp::LibraryProduct, prefix::Prefix;
       env::Dict{String,String},
       verbose::Bool = false)
```

指定されたライブラリが存在し（合理的な名前の下で）、`dlopen()`可能である場合（現在のプラットフォーム用にビルドされていると仮定）、その場所を返します。`dlopen()`テストは、現在のプラットフォームが指定された`platform`キーワード引数と一致する場合にのみ実行されることに注意してください。クロスコンパイルされたライブラリは、外国のプラットフォームでは`dlopen()`できません。
