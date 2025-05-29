```
get_maximum_request_length(conn:: XCBConnection) -> UInt32
```

XCBドキュメントから:

> BIG-REQUESTS拡張がない場合、接続セットアップデータから最大リクエスト長フィールドを返します。これは最大65535までです。サーバーがBIG-REQUESTSをサポートしている場合、BigRequestsEnableリクエストへの応答から最大リクエスト長フィールドが返されます。
>
> この長さは4バイト単位で測定されるため、BIG-REQUESTSなしでの理論的最大長は約256kB、BIG-REQUESTSありで16GBです。

