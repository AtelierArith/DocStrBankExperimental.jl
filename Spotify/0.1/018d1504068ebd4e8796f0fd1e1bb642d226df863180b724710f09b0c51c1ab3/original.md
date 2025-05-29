All web API arguments are strings, but types  `SpUri`, `SpId`, `CategoryId`, `SpUserId`, `SpUrl`  aids in picking default values. [format]( https://developer.spotify.com/documentation/web-api/#spotify-uris-and-ids)

|  PARAMETER   | DESCRIPTION                                                     |            VALUE             |
|:------------:|:--------------------------------------------------------------- |:----------------------------:|
|    SpUri     | The resource identifier that you can enter, for example, in the |                              |
|              | Spotify Desktop client’s search box to locate an artist,        |                              |
|              | album, or track. To find a Spotify URI simply right-            |                              |
|              | click (on Windows) or Ctrl-Click (on a Mac) on                  |        spotify:track:        |
|              | the artist’s or album’s or track’s name.                        |    6rqhFgbbKwnb9MLmUQDhG6    |
|     SpId     | The base-62 identifier that you can find at the end of the      |                              |
|              | Spotify URI (see above) for an artist, track, album,            |                              |
|              | playlist, etc. Unlike a Spotify URI, a Spotify ID does          |                              |
|              | not clearly identify the type of resource; that information is  |                              |
|              | provided elsewhere in the call.                                 |    6rqhFgbbKwnb9MLmUQDhG6    |
| SpCategoryId | The unique string identifying the Spotify category.             |            party             |
|   SpUserId   | The unique string identifying the Spotify user that you can     |                              |
|              | find at the end of the Spotify URI for the user. The ID         |                              |
|              | of the current user can be obtained via the Web API endpoint.   |           wizzler            |
|    SpUrl     | An HTML link that opens a track, album, app, playlist or other  |                              |
|              | Spotify resource in a Spotify client (which  client             |                              |
|              | is determined by the user’s device and                          |   http://open.spotify.com/   |
|              | account settings at play.spotify.com.                           | track/6rqhFgbbKwnb9MLmUQDhG6 |
