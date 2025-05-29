```
sharerequestinfo(client::PCloudClient; kwargs...)
```

ユーザーのメールに送信された `code` から共有リクエストの情報を取得します。

ソース: https://docs.pcloud.com/methods/sharing/sharerequestinfo.html

# 引数

  * `code::String`: ユーザーのメールに送信されたコード

# 出力

共有に関する情報を返します。

# 出力例

```
{
    result: 0,
    share: {
        tomail: "pcloud@pcloud.com",
        cancreate: false,
        folderid: 21385,
        sharerequestid: ID,
        canread: true,
        expires: "Thu, 24 Oct 2013 10:41:29 +0000",
        canmodify: false,
        message: "The message",
        candelete: false,
        sharename: "My Share",
        created: "Thu, 03 Oct 2013 10:41:29 +0000"
    }
}
```
