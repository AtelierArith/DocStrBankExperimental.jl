```
get_news_for_app(appid::Int;
    maxlength::Int=0,
    enddate::DateTime=now(),
    count::Int=20,
    feeds::Vector{String}=String[],
    tages::Vector{String}=String[])::Appnews
```

**概要**: `get_news_for_app` は、指定された AppID のゲームの最新情報を返します。

# 引数

  * `appid`: ニュースを取得したいゲームの AppID。

# オプションのキーワード

  * `maxlength`: 各ニュースエントリの最大長。
  * `enddate`: この日付よりも前の投稿を取得します（unix エポックタイムスタンプ）
  * `count`: 返されるニュースエントリの数。
  * `feeds`: ニュースを取得するためのフィード名のカンマ区切りリスト
  * `tages`: フィルタリングするためのタグのカンマ区切りリスト（例: 'patchnodes'）

# 例

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
