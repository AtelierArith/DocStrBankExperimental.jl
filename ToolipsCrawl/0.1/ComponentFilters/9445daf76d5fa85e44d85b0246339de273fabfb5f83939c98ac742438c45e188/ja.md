2022年12月に作成された [chifi - an open source software dynasty.](https://github.com/orgs/ChifiSource)

  * このソフトウェアはMITライセンスです。

### ComponentFilters

**ComponentFilters** は、`Toolips` の `Vector{Servable}` 型のためのいくつかのシンプルなプレメイドフィルターを提供します。このモジュールは、`Component` の側面に基づいて値を取得するために `Toolips.get` を拡張します。このモジュールは3つのデフォルトフィルターを提供します：

  * `ComponentFilters.bytag`
  * `ComponentFilters.byname`
  * `ComponentFilters.has_property`

```example
comps = scrape("https://github.com/ChifiSource") do c::Crawler
    comps = c[ComponentFilters.bytag, "img"]
    get(comps, ComponentFilters.has_property, "src")
end
```

新しいフィルターを実装するのは簡単です。`get(::ComponentFilter{<:Any}, ::Vector{Servable})` を拡張するだけです。

```example
using Toolips
using ToolipsCrawl
import Toolips: get

function get(f::ComponentFilter{:images}, comps::Vector{Servable})
    comps = get(ComponentFilters.bytag, "img")
    get(CompFilters.has_property, "src")
end
```
