```
search_pinyin(dict, keyword)
```

辞書で提供されたピンイン検索キーにあいまいに一致する用語を検索します。検索キーに対して理解される言語は以下に説明されています。

# 例

```julia-repl
julia> search_pinyin(dict, "yi2 han4") .|> println;
遺憾 (遗憾): [yi2 han4]
        regret
        to regret
        to be sorry that

julia> search_pinyin(dict, "bang shou") .|> println;
榜首: [bang3 shou3]
        top of the list
幫手 (帮手): [bang1 shou3]
        helper
        assistant
```
