```
suggest_alternative_kws(kws, possible_kws; n_suggestions = 3, cutoff = 0.6)
```

代替キーワードを提案します。ここで、`kws`は関数に渡されたキーワード名のリストであり、`possible_kws`は真のキーワード名のリストです。これらはシンボルまたは文字列である必要があります。これは、`keys(kws)`を使用して関数`kws`から取得できます。

# 例

```julia
function f(; kws...)
    msg = suggest_alternative_kws(keys(kws), [:kw1, :kw2])
    if isempty(msg)
        return "すべてのキーワードは有効です"
    else
        return "無効なキーワードをいくつか受け取りました。エラーは次のとおりです:" * msg
    end
end
```
