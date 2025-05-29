```
set_locale!([gloc::Locale, ]locale::LocaleId[, category::CategorySet])
```

Set contents of locale in selected categories. Missing category or :ALL sets all defined categories to the same locale. If `gloc` is not given, the current task-specific locale is used. Throw exception if category is not :ALL or one of the supported categories of `locale`.
