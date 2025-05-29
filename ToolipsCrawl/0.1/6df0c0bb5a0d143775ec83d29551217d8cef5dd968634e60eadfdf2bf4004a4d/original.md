### Crawler <: AbstractCrawler

  * address**::String**
  * crawling**::Bool**
  * addresses**::Vector{String}**
  * components**::Vector{Servable}**

---

The `Crawler` is created by the functions `crawl` and `scrape` and stores components from addresses while navigating  to new ones while crawling.  A `Crawler` will be passed through a `Function` provided to `scrape` or `crawl` as an argument.

```example
using ToolipsCrawl
subtitletxt = scrape("https://github.com/ChifiSource/ToolipsCrawl.jl") do c::Crawler
    text = c["start-of-content"]["class"]
end
```

Indexing with a `String` will yield the `Component` by that name. A `Crawler` may be stopped with `kill!`.  For more information on `scrape` or `crawl`, see `?scrape` and `?crawl` respectively. Crawlers may also be  filtered using `ComponentFilters`. We are able to filter by getting index with a filter and a value to filter with. This allows us to get elements by name, by tag, or elements that contain a certain property.

```example
using ToolipsCrawl
using Toolips
comps = scrape("https://github.com/ChifiSource") do c::Crawler
    comps = c[ComponentFilters.bytag, "img"]
    get(comps, ComponentFilters.has_property, "src")
end
```

## For more information on these filters, see `?ComponentFilters`

##### constructors

  * Crawler(address::String)
