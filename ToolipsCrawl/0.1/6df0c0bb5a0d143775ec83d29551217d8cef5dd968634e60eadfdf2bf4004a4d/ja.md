### Crawler <: AbstractCrawler

  * address**::String**
  * crawling**::Bool**
  * addresses**::Vector{String}**
  * components**::Vector{Servable}**

---

`Crawler`は、`crawl`および`scrape`関数によって作成され、クローリング中に新しいアドレスに移動しながらアドレスからコンポーネントを保存します。`Crawler`は、`scrape`または`crawl`に引数として提供された`Function`を通じて渡されます。

```example
using ToolipsCrawl
subtitletxt = scrape("https://github.com/ChifiSource/ToolipsCrawl.jl") do c::Crawler
    text = c["start-of-content"]["class"]
end
```

`String`でインデックスを付けると、その名前の`Component`が得られます。`Crawler`は`kill!`で停止することができます。`scrape`または`crawl`に関する詳細は、それぞれ`?scrape`および`?crawl`を参照してください。クローラーは`ComponentFilters`を使用してフィルタリングすることもできます。フィルタとフィルタリングする値を使ってインデックスを取得することで、名前、タグ、または特定のプロパティを含む要素を取得することができます。

```example
using ToolipsCrawl
using Toolips
comps = scrape("https://github.com/ChifiSource") do c::Crawler
    comps = c[ComponentFilters.bytag, "img"]
    get(comps, ComponentFilters.has_property, "src")
end
```

## これらのフィルタに関する詳細は、`?ComponentFilters`を参照してください

##### コンストラクタ

  * Crawler(address::String)
