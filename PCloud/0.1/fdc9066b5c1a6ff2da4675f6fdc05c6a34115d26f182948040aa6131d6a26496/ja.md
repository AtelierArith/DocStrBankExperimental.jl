```
getfilehistory(client::PCloudClient; kwargs...)
```

`fileid`で識別されるファイルのイベント履歴を返します。ファイルは削除されたものである可能性があります。出力形式はdiffメソッドと同じです。

ソース: https://docs.pcloud.com/methods/general/getfilehistory.html

# 引数

  * `fileid::Int`: 履歴が要求されるファイルのfileid

# 出力例

```
{
  "result": 0,
  "entries": [
    {
      "event": "createfile",
      "time": "Mon, 14 Oct 2013 03:24:43 +0000",
      "diffid": 13924,
      "metadata": {
        "isshared": true,
        "thumb": false,
        "contenttype": "video/mp4",
        "size": 0,
        "category": 2,
        "hash": 14841775194319522618,
        "parentfolderid": 397140,
        "modified": "Mon, 14 Oct 2013 03:24:43 +0000",
        "isfolder": false,
        "created": "Mon, 14 Oct 2013 03:24:43 +0000",
        "fileid": 2712167,
        "id": "f2712167",
        "icon": "video",
        "name": "GOPR0002.MP4",
        "ismine": true
      }
    },
    {
      "event": "modifyfile",
      "time": "Mon, 14 Oct 2013 04:07:25 +0000",
      "diffid": 13927,
      "metadata": {
        "isshared": true,
        "thumb": true,
        "contenttype": "video/mp4",
        "size": 1993278633,
        "category": 2,
        "hash": 4322830267003041431,
        "parentfolderid": 397140,
        "modified": "Mon, 14 Oct 2013 04:07:25 +0000",
        "isfolder": false,
        "created": "Mon, 14 Oct 2013 03:24:43 +0000",
        "fileid": 2712167,
        "id": "f2712167",
        "icon": "video",
        "name": "GOPR0002.MP4",
        "ismine": true
      }
    }
  ]
}
```
