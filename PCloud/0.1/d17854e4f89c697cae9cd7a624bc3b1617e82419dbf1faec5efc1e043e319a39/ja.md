```
createuploadlink(client::PCloudClient; kwargs...)
```

アップロードリンクを作成します。

アップロードされたファイルが保存されるフォルダの `folderid`/`path` を期待します。フォルダはユーザーが所有している必要があります。共有は他のユーザーからの確認が必要な場合があります。

共有されるフォルダは `folderid` または `path` で特定されます。

また、アップロードユーザーに提供したいコメントや指示を含む `comment` パラメータを持つべきです。コメントはアップロードユーザーが見る唯一の情報です（彼らは所有者のユーザー名やアップロード先のフォルダ名を知ることはありません）ので、実装はユーザーに対して、アップローダーに期待される内容の少なくともいくつかの説明を記入するよう指示するべきです（例：こんにちは、マイクです。私の結婚式で撮った写真をここにアップロードしてください。）。

オプションのパラメータ `expire` は、リンクが機能しなくなる日時を示すことができます。

また、オプションで `maxspace` と `maxfiles` は、アップロードできる最大の合計サイズ（バイト単位）とファイルの総数を制限することができます。

出典: https://docs.pcloud.com/methods/upload_links/createuploadlink.html

# 引数

  * `folderid::Int`: アップロードされたファイルが保存されるフォルダのフォルダID
  * `path::String`: アップロードされたファイルが保存される共有フォルダへのパス
  * `comment::String`: アップロードユーザーに提供したいコメント

`path` または `folderid` を使用してください。

# オプション引数

  * `expire::datetime`: リンクが機能しなくなる日時。
  * `maxspace::Int`: 最大合計サイズ（バイト単位）を制限
  * `maxfiles::Int`: アップロードできるファイルの総数

# 出力

成功した場合、次のものを返します。

  * `uploadlinkid::Int`: このリンクを変更/削除するために使用できます
  * `link::String`: ファイルをアップロードできるページへの完全なリンク
  * `mail::String`: このリンクにファイルをアップロードするためにも使用できるメールアドレス
  * `code::String`: ファイルをアップロードするために使用できるリンクのコード。

{

"result": 0,

"code": "linkCode",

"mail": "somewhere@u.pcloud.com",

"uploadlinkid": linkID,

"link": "https://my.pcloud.com/#page=puplink&code=linkCode"

}
