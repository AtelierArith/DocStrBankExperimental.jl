```
confirm_yn(question::AbstractString, default::Bool=false)
```

インタラクティブに `question` を尋ね、y/Y/n/N を応答として受け付けます。他のキーが押された場合、`default` が応答として取られます。質問には " [y/n]: " という文字列が追加され、y/n はデフォルト値を示すために大文字になります。

### 例

```julia-repl
julia> confirm_yn("チョコレートは好きですか？", true)
チョコレートは好きですか？ [Y/n]: y
true
```
