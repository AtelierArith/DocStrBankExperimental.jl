```
uploadfile(client::PCloudClient; kwargs...)
```

ファイルをアップロードします。

文字列 `path` または整数 `folderid` でターゲットディレクトリを指定します。両方が省略された場合、ルートフォルダが選択されます。

パラメータ文字列 `progresshash` を渡すことができます。同じものを uploadprogress メソッドに渡す必要があります。

`nopartial` が設定されている場合、部分的にアップロードされたファイルは保存されません（これは、接続が切れる前にファイルが完全に読み込まれない場合です）。`renameifexists` が設定されている場合、名前の競合が発生したときに、ファイルは上書きされず、`filename (2).ext` のように名前が変更されます。

複数のファイルをアップロードすることができ、`multipart/form-data` エンコーディングを使用して POST します。POST で渡された場合、パラメータはファイルの前に来る必要があります。すべてのファイルが受け入れられ、フォームフィールドの名前は無視されます。複数のファイルは、1つ以上の HTML ファイルコントロールから来ることができます。

ファイル名は、各ファイルの `filename` プロパティとして渡す必要があります。つまり、ブラウザがファイル名を送信する方法です。

同じ名前のファイルがすでにディレクトリに存在する場合、それは上書きされ、古いものはリビジョンとして保存されます。同じデータでファイルを上書きしても、ファイルの `modification time` を更新する以外は何も行われません。

出典: https://docs.pcloud.com/methods/file/uploadfile.html

# 引数

  * `path::String`: フォルダへのパス（推奨されません）
  * `folderid::Int`: フォルダの ID
  * `filename::String`: アップロードされた各ファイルのファイル名

# オプション引数

  * `nopartial::Int`: 設定されている場合、部分的にアップロードされたファイルは保存されません
  * `progresshash::String`: アップロード進行状況を観察するために使用されるハッシュ
  * `renameifexists::Int`: 設定されている場合、要求された名前のファイルがフォルダに存在する場合、アップロードされたファイルは名前が変更されます。
  * `mtime::Int`: 設定されている場合、ファイルの修正時間が設定されます。Unix 時間の秒である必要があります。
  * `ctime::Int`: 設定されている場合、ファイルの作成時間が設定されます。ctime を設定するには mtime を提供する必要があります。Unix 時間の秒である必要があります。

# 出力

2つの配列 - fileids と `metadata` を返します。

# 出力例

```
{
    "result": 0,
    "fileids": [
        1729212
    ],
    "metadata": [
        {
          "ismine": true,
          "id": "f1729212",
          "created": "Wed, 02 Oct 2013 14:29:11 +0000",
          "modified": "Wed, 02 Oct 2013 14:29:11 +0000",
          "hash": 10681749967730527559,
          "isshared": false,
          "isfolder": false,
          "category": 1,
          "parentfolderid": 0,
          "icon": "image",
          "fileid": 1729212,
          "height": 600,
          "width": 900,
          "path": "/Simple image.jpg",
          "name": "Simple image.jpg",
          "contenttype": "image/jpeg",
          "size": 73269,
          "thumb": true
        }
    ]
}

```
