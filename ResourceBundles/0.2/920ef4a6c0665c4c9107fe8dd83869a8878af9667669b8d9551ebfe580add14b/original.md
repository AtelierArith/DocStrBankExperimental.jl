```
string_to_key(text::AbstractString)
```

Convert text to key. Replace interpolation syntax with standardized interpoleated integers. Example without explicit primarity:     `string_to_key("text$var $(expr) $(77)") == "text1 2 3"` Example with explicit primarity:     `string_to_key("text$var $(!(expr)) $(77)") == "text2 1 3"` (The first interpolation annotated with '`!`' gets number 1). The interpolation must not be a literal string.
