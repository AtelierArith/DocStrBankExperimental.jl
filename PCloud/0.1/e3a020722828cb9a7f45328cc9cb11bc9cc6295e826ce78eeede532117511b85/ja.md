```
getdigest(client::PCloudClient; kwargs...)
```

ダイジェスト認証のためのダイジェストを返します。ダイジェストは30秒間有効です。

ソース: https://docs.pcloud.com/methods/general/getdigest.html

# 出力

  * `digest::String`: 認証用のダイジェスト
  * `expires::datetime`: ダイジェストの有効期限

# 出力例

```
{
    result: 0,
    digest: "YGtAxbUpI85Zvs7lC7Z62rBwv907TBXhV2L867Hkh",
    expires: "Fri, 27 Sep 2013 10:15:46 +0000"
}
```
