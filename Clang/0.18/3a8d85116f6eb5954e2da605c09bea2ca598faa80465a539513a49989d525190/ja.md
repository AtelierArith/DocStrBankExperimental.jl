```
spelling(tu::TranslationUnit, t::CLToken) -> String
spelling(tu::TranslationUnit, t::CXToken) -> String
spelling(tu::CXTranslationUnit, t::CXToken) -> String
```

与えられたトークンのスペルを返します。トークンのスペルは、そのトークンのテキスト表現です。例えば、識別子やキーワードのテキストです。
