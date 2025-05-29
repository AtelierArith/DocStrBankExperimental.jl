```julia
scrape(f::Function, address::String, components::String ...) -> ::Any
```

---

`components`のコンポーネント名のみを`address`でスクレイピングし、`Address`から`f`にコンポーネントを持つ`Crawler`を提供します。`example subtitletxt = scrape("https://github.com/ChifiSource/ToolipsCrawl.jl", "start-of-content") do c::Crawler     text = c["start-of-content"]["class"] end``
