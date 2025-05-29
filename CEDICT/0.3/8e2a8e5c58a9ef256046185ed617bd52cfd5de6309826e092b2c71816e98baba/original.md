```
search_pinyin(dict, keyword)
```

Search the dictionary for terms that fuzzy match the pinyin search key provided. The language that is understood for the search key is described below.

# Examples

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
