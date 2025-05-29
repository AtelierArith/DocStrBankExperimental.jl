```julia
crawl(f::Function, address::String ...) -> ::Crawler
```

---

`crawl` scrapes each `address` then calls `f` on a `Crawler` with the scraped components, then crawls to addresses found on  that page, repeating the function call until `kill!` is used or there are no remaining addresses. ```example using Toolips using ToolipsCrawl

# collects images forever

images = Vector{Servable}() newdiv = div("parentcont"); newdiv[:children] = images i = 0 crawler1 = crawl("https://github.com/ChifiSource") do c::Crawler     f = findall(comp -> comp.tag == "img", c.components)     [begin         comp = c.components[position]         if "src" in keys(comp.properties)             image = img("ex", src = comp["src"], width = 50)             style!(image, "display" => "inline-block")             push!(images, image)         end     end for position in f] end @async while crawler1.crawling     display(newdiv)     sleep(5) end ````
