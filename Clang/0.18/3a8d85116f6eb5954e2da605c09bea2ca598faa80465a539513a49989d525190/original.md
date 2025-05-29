```
spelling(tu::TranslationUnit, t::CLToken) -> String
spelling(tu::TranslationUnit, t::CXToken) -> String
spelling(tu::CXTranslationUnit, t::CXToken) -> String
```

Return the spelling of the given token. The spelling of a token is the textual representation of that token, e.g., the text of an identifier or keyword.
