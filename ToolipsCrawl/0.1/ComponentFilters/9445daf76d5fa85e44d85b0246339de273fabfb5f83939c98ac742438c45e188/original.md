Created in December, 2022 by [chifi - an open source software dynasty.](https://github.com/orgs/ChifiSource)

  * This software is MIT-licensed.

### ComponentFilters

**ComponentFilters** provides some simple premade filters for the `Vector{Servable}` type from `Toolips`. This module extends `Toolips.get` to pull values based on aspects of a `Component`. This module provides three  default filters:

  * `ComponentFilters.bytag`
  * `ComponentFilters.byname`
  * `ComponentFilters.has_property`

```example
comps = scrape("https://github.com/ChifiSource") do c::Crawler
    comps = c[ComponentFilters.bytag, "img"]
    get(comps, ComponentFilters.has_property, "src")
end
```

Implementing a new filter is simple; just extend `get(::ComponentFilter{<:Any}, ::Vector{Servable})`.

```example
using Toolips
using ToolipsCrawl
import Toolips: get

function get(f::ComponentFilter{:images}, comps::Vector{Servable})
    comps = get(ComponentFilters.bytag, "img")
    get(CompFilters.has_property, "src")
end
```
