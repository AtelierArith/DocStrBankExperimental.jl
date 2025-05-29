### ToolipsCrawl

```julia
scrape(f::Function, address::String) -> ::Any
```

---

Scrapes `address`, providing a `Crawler` with components from `Address` to `f`. ```example subtitletxt = scrape("https://github.com/ChifiSource/ToolipsCrawl.jl") do c::Crawler     text = c["start-of-content"]["class"] end

myimage = scrape("https://google.com") do c::Crawler     googlelogo = findfirst(comp -> comp.tag == "img", c.components)     img("googlelogo", src = "https://google.com" * c.components[googlelogo]["src"]) end ````
