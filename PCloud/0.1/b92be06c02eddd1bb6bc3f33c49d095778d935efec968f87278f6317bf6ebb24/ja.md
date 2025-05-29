```
showpublink(client::PCloudClient; kwargs...)
```

パラメータ `code` は 'code' または 'shortcode' のいずれかである必要があります。

`code` は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/showpublink.html

# 引数

  * `code::String`: 'code' または 'shortcode' のいずれか

# 出力

リンクが指すオブジェクトの `metadata` を返します。

オブジェクトがフォルダの場合、`contents` フィールドが存在し（listfolder のように）、フォルダの（再帰的な）内容が含まれます。

返される `metadata` の `isshared` フィールドは、ファイル/フォルダの実際の共有状態に関係なく、常に `false` です。

# 出力例

```
{
    result: 0,
    metadata: {
        isshared: false,
        icon: "folder",
        modified: "Wed, 18 Sep 2013 10:25:57 +0000",
        name: "Simple folder",
        id: "d21721",
        folderid: 21721,
        ismine: true,
        isfolder: true,
        created: "Wed, 18 Sep 2013 10:18:14 +0000",
        thumb: false,
        contents: [
            {
                icon: "audio",
                fileid: 618279,
                parentfolderid: 21721,
                size: 17675824,
                category: 3,
                isfolder: false,
                thumb: true,
                isshared: false,
                ismine: true,
                modified: "Wed, 18 Sep 2013 10:19:05 +0000",
                name: "Simple Audio.mp3",
                artist: "Pcloud",
                trackno: 1,
                genre: "Genre",
                contenttype: "audio/mpeg",
                title: "Simple Audio",
                album: "The album",
                id: "f618279",
                created: "Wed, 18 Sep 2013 10:18:15 +0000",
                hash: 6343095883282229000
            },
            ...
        ]
    }
}
```
