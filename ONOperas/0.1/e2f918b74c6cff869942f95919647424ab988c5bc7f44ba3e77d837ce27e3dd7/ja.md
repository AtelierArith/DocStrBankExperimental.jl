```
scrape_operas(base_urls::Vector{String};
              pages::Integer = 1,
              save_to::Union{Nothing,AbstractString} = nothing)
```

各 `base_urls` の下にリストされているオペラのメタデータを取得し、ページ 1 から `pages` までを繰り返します。次の列を持つ DataFrame を返します：

• オペラ名     • 初演日     • 作曲家     • リブレット作家・文学・ソース     • ジャンル     • 都市     • 州・地域     • 国     • 劇場  

`save_to` がファイルパス（例：`"data/italy.csv"`）の場合、DataFrame は返される前にその CSV にも書き込まれます。
