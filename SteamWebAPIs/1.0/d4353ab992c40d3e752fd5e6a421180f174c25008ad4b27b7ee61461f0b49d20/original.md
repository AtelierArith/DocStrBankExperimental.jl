```
get_news_for_app(appid::Int;
    maxlength::Int=0,
    enddate::DateTime=now(),
    count::Int=20,
    feeds::Vector{String}=String[],
    tages::Vector{String}=String[])::Appnews
```

**Summary**: `get_news_for_app` returns the latest of a game specified by its AppID.

# Arguments

  * `appid`: AppID of the game you want the news of.

# Optional keywords

  * `maxlength`: Maximum length of each news entry.
  * `enddate`: Retrieve posts earlier than this date (unix epoch timestamp)
  * `count`: How many news enties you want to get returned.
  * `feeds`: Comma-separated list of feed names to return news for
  * `tages`: Comma-separated list of tags to filter by (e.g. 'patchnodes')

# Example

```julia-repl
julia> dump(get_news_for_app(440;maxlength=10,enddate=now(),count=1,feeds=["steam_updates","tf2_blog"]))
SteamWebAPIs.Appnews
  appid: Int64 440
  newsitems: Array{SteamWebAPIs.NewsItem}((1,))
    1: SteamWebAPIs.NewsItem
      gid: Int64 5759616966668990190
      title: String "Fireside Cup"
      url: String "https://steamstore-a.akamaihd.net/news/externalpost/steam_community_announcements/5759616966668990190"
      is_external_url: Bool true
      author: String "erics"
      contents: String "{STEAM_CLA..."
      feedlabel: String "Community Announcements"
      date: Dates.DateTime
        instant: Dates.UTInstant{Dates.Millisecond}
          periods: Dates.Millisecond
            value: Int64 63849838959000
      feedname: String "steam_community_announcements"
      feed_type: Int64 1
      tags: Nothing nothing
  count: Int64 3545
```
