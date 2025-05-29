```julia
scrape(f::Function, address::String, components::String ...) -> ::Any
```

---

Scrapes only component names in `components` at `address`, providing a `Crawler` with components from `Address` to `f` `example subtitletxt = scrape("https://github.com/ChifiSource/ToolipsCrawl.jl", "start-of-content") do c::Crawler     text = c["start-of-content"]["class"] end``
