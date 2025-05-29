```
install_atomize_mode(;
    start_key = "\M-a", prompt_text = "atomize> ", prompt_color = :cyan,
kwargs...)
```

`atomize` REPLモードをインストールします。このモードでは、入力が暗黙的に[`@atomize`](@ref)で始まります。

キーワード引数は[`ReplMaker.initrepl`](https://github.com/MasonProtter/ReplMaker.jl)に渡されます。デフォルトのスタートキーは、[Meta]（[Alt]とも呼ばれる）キーと[a]キーを同時に押すことです。利用可能な`prompt_color`は`Base.text_colors`にあります。
