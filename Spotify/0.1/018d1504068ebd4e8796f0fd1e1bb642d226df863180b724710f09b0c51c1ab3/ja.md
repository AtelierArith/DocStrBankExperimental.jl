すべてのWeb API引数は文字列ですが、`SpUri`、`SpId`、`CategoryId`、`SpUserId`、`SpUrl`の型はデフォルト値を選択するのに役立ちます。[format]( https://developer.spotify.com/documentation/web-api/#spotify-uris-and-ids)

|    パラメーター    | 説明                                                                          |              値               |
|:------------:|:--------------------------------------------------------------------------- |:----------------------------:|
|    SpUri     | アーティスト、アルバム、またはトラックを見つけるために、たとえば、Spotifyデスクトップクライアントの検索ボックスに入力できるリソース識別子です。 |                              |
|              | Spotify URIを見つけるには、単に右クリック（Windowsの場合）またはCtrl-クリック（Macの場合）して、               |        spotify:track:        |
|              | アーティスト、アルバム、またはトラックの名前をクリックします。                                             |    6rqhFgbbKwnb9MLmUQDhG6    |
|     SpId     | アーティスト、トラック、アルバム、プレイリストなどのSpotify URIの末尾にあるbase-62識別子です。                    |                              |
|              | （上記参照）Spotify URIとは異なり、Spotify IDはリソースのタイプを明確に識別しません。                       |                              |
|              | その情報は呼び出しの他の場所で提供されます。                                                      |    6rqhFgbbKwnb9MLmUQDhG6    |
| SpCategoryId | Spotifyカテゴリを識別するユニークな文字列です。                                                 |            party             |
|   SpUserId   | ユーザーのSpotify URIの末尾にあるSpotifyユーザーを識別するユニークな文字列です。                           |                              |
|              | 現在のユーザーのIDはWeb APIエンドポイントを介して取得できます。                                        |           wizzler            |
|    SpUrl     | トラック、アルバム、アプリ、プレイリスト、または他のSpotifyリソースをSpotifyクライアントで開くHTMLリンクです。            |                              |
|              | （どのクライアントが使用されるかは、ユーザーのデバイスと                                                |   http://open.spotify.com/   |
|              | アカウント設定によって決まります。）                                                          | track/6rqhFgbbKwnb9MLmUQDhG6 |
