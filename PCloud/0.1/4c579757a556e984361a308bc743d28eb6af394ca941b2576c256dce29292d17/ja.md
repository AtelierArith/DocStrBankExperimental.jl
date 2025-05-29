```
uploadtolink(client::PCloudClient; kwargs...)
```

アップロードリンクにファイルをアップロードします。`code`を期待します。

uploadfileに適用されるほとんどのことはここにも適用されます。特に、`progresshash`はuploadlinkprogressを使用してアップロードの進行状況を監視するために同様の方法で使用できます。

`renameifexists`が省略されているというわずかな違いがあり、アップロードリンクに要求された名前のファイルが存在する場合、アップロードされたファイルは常に名前が変更されます。

ソース: https://docs.pcloud.com/methods/upload_links/uploadtolink.html

# 引数

  * `code::String`: リンクのコード

# オプション引数

  * `nopartial::Int`: 設定されている場合、部分的にアップロードされたファイルは保存されません
  * `progresshash::String`: アップロードの進行状況を観察するために使用されるハッシュ

# 出力例

```
{
    result: 0
}
```
