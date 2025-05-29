```
sublevelalias!(I::Ion, aliasassignments)
```

`aliasassignments` は、どのエイリアスがどのサブレベルに割り当てられるべきかを指定します。これを行うための2つのオプションがあります：

  * `aliasassignments` はタプルのベクターであり、各タプルの最初の要素がサブレベル（`sublevel::Tuple{String,Real}`）で、2番目の要素がその割り当てられたエイリアス（`alias::String`）です。
  * `aliasassignments` は、フォーマット `alias::String => sublevel::Tuple{String,Real}` の辞書です。

各ペア `sublevel, alias` に対して `sublevelalias!(I, sublevel, alias)` を呼び出します。
