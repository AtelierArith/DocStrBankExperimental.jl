### ToolipsCrawl

```julia
scrape(f::Function, address::String) -> ::Any
```

---

`address`をスクレイピングし、`Address`から`f`にコンポーネントを提供する`Crawler`を作成します。 ```example subtitletxt = scrape("https://github.com/ChifiSource/ToolipsCrawl.jl") do c::Crawler     text = c["start-of-content"]["class"] end

myimage = scrape("https://google.com") do c::Crawler     googlelogo = findfirst(comp -> comp.tag == "img", c.components)     img("googlelogo", src = "https://google.com" * c.components[googlelogo]["src"]) end ````
