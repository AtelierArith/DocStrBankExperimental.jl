```
LocaleId(languagetag::String))
LocaleId(lang, region)
LocaleId(lang, script, region)
LocaleId(lang, script, region, variant)
LocaleId("") -> DEFAULT
LocaleId() -> BOTTOM
```

Return `LocaleId` object from cache or create new one and register in cache.
