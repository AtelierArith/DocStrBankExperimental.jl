```julia
crawl(f::Function, address::String ...) -> ::Crawler
```

---

`crawl` は各 `address` をスクレイピングし、スクレイピングしたコンポーネントを持つ `Crawler` に対して `f` を呼び出し、そのページで見つかったアドレスにクロールし、`kill!` が使用されるか、残りのアドレスがない限り関数呼び出しを繰り返します。 ```example using Toolips using ToolipsCrawl

# 永遠に画像を収集します

images = Vector{Servable}() newdiv = div("parentcont"); newdiv[:children] = images i = 0 crawler1 = crawl("https://github.com/ChifiSource") do c::Crawler     f = findall(comp -> comp.tag == "img", c.components)     [begin         comp = c.components[position]         if "src" in keys(comp.properties)             image = img("ex", src = comp["src"], width = 50)             style!(image, "display" => "inline-block")             push!(images, image)         end     end for position in f] end @async while crawler1.crawling     display(newdiv)     sleep(5) end ```
