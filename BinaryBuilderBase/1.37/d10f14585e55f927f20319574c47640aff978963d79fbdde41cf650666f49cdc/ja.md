```
expand_cxxstring_abis(p::AbstractPlatform; skip=Sys.isbsd)
```

与えられた `Platform` に対して、`Platform` オブジェクト内の `cxxstring_abi` タグを除いて同一のエントリを持つ `Platforms` の配列を返します。これは、例えば、サポートされているプラットフォームのリストを取得し、ABI マッチングの目的で複数の GCC バージョンを含むように展開するために使用されます。

指定された `Platform` がすでに `cxxstring_abi` を指定している場合（`nothing` ではなく）、その `Platform` のみが返されます。`skip` が関数であり、`skip(platform)` が `true` に評価される場合、指定されたプラットフォームは展開されません。デフォルトでは、FreeBSD および macOS プラットフォームは、`libstdc++` に依存しておらず、この互換性シムが必要ないため、スキップされます。
