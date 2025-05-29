```julia
parse_file(
    file::String;
    import_all,
    validate,
    correct_branch_rating
) -> Any

```

```
parse_file(
    file;
    import_all = false,
    validate = true,
    correct_branch_rating = true,
)
```

Matpower .m `file` または PTI (PSS(R)E-v33) .raw `file` を PowerModels データ構造に解析します。`import_all` が true の場合、PTI ファイルのすべてのフィールドがインポートされます（デフォルト: false）。
