```
struct RequestError <: ErrorException
    url      :: String
    code     :: Int
    message  :: String
    response :: Response
end
```

`RequestError` は、例外オブジェクトとしてリクエストに対する失敗したレスポンスのプロパティをキャプチャする型です：

  * `url`: リダイレクトなしでリクエストされた元のURL
  * `code`: libcurlエラーコード; プロトコル専用のエラーが発生した場合は `0`
  * `message`: 何が問題だったのかを示すlibcurlエラーメッセージ
  * `response`: 利用可能なレスポンス情報をキャプチャするレスポンスオブジェクト

同じ `RequestError` 型は、リクエストが成功したが、2xx範囲外のステータスコードによってプロトコルレベルのエラーが示された場合に `download` によってスローされます。この場合、`code` はゼロになり、`message` フィールドは空の文字列になります。`request` API は、libcurlエラー `code` がゼロでない場合にのみ `RequestError` をスローします。この場合、含まれる `response` オブジェクトは、`status` がゼロでメッセージが空である可能性が高いです。ただし、プロトコルエラーによってcurlレベルのエラーがスローされる状況もあり、その場合は内部および外部のコードとメッセージの両方が関心の対象となるかもしれません。
