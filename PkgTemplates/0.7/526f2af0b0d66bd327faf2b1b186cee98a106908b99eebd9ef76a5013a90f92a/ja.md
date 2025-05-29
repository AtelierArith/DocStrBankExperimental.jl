```
Secret(name::AbstractString)
```

GitHubリポジトリのシークレットを表します。文字列に変換されると、`${{ secrets.<name> }}`を返します。
