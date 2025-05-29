```
LocaleId(languagetag::String))
LocaleId(lang, region)
LocaleId(lang, script, region)
LocaleId(lang, script, region, variant)
LocaleId("") -> DEFAULT
LocaleId() -> BOTTOM
```

キャッシュから `LocaleId` オブジェクトを返すか、新しいものを作成してキャッシュに登録します。
