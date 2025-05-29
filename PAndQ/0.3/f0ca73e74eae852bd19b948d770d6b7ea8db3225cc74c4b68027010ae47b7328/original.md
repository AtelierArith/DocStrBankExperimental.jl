```
install_atomize_mode(;
    start_key = "\M-a", prompt_text = "atomize> ", prompt_color = :cyan,
kwargs...)
```

Install the `atomize` REPL mode, where input implicitly begins with [`@atomize`](@ref).

Keyword arguments are passed to [`ReplMaker.initrepl`](https://github.com/MasonProtter/ReplMaker.jl). The default start keys are pressing both the [Meta] (also known as [Alt]) and [a] keys at the same time. The available `prompt_color`s are in `Base.text_colors`.
