```
read_struct(oh, type_func, size_func, name)
```

与えられた `Type`（例えば `ELFSection64`）から、指定されたオブジェクトを `unpack()` し、それを返します。適切なエラーを投げ、`type_func` と `size_func` によって決定された余分なパディングバイトをスキップします。例の呼び出し:

read*struct(oh, symtab*entry*type, symtab*entry_size, "Symbol Entry")
