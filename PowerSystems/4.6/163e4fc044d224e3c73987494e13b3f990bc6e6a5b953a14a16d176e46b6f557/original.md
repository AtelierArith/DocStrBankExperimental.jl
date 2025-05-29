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

Parses a Matpower .m `file` or PTI (PSS(R)E-v33) .raw `file` into a PowerModels data structure. All fields from PTI files will be imported if `import_all` is true (Default: false).
