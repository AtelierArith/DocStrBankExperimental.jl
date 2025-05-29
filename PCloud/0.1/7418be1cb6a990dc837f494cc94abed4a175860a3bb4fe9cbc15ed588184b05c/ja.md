```
listshares(client::PCloudClient; kwargs...)
```

現在の共有と共有リクエストをリストします。

ソース: https://docs.pcloud.com/methods/sharing/listshares.html

# オプション引数

  * `norequests::Int`: 設定されている場合、共有リクエストは返されません
  * `noshares::Int`: 設定されている場合、確立された共有は返されません
  * `noincoming::Int`: 設定されている場合、結果に受信サブオブジェクトは表示されません
  * `nooutgoing::Int`: 設定されている場合、結果に送信サブオブジェクトは表示されません

# 出力

`shares` と `requests` の2つのオブジェクトを返し、どちらもサブオブジェクト `incoming` と `outgoing` を持ちます。

# 出力例

```
{
    result: 0,
    shares: {
        incoming: [ ],
        outgoing: [ ]
    },
    requests: {
        incoming: [ ],
        outgoing: [
            {
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
        ]
    }
}
```
