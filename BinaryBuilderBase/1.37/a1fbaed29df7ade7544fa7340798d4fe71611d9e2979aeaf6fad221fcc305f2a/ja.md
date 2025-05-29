```
expand_gfortran_versions(p::AbstractPlatform)
```

与えられた `Platform` に対して、`Platform` 内の `libgfortran_version` タグを除いて同一のエントリの配列を返します。これは、例えば、サポートされているプラットフォームのリストを取得し、ABI マッチングの目的で複数の GCC バージョンを含むように展開するために使用されます。与えられた `Platform` がすでに `libgfortran_version` を指定している場合（`nothing` ではなく）、その `Platform` のみが返されます。
