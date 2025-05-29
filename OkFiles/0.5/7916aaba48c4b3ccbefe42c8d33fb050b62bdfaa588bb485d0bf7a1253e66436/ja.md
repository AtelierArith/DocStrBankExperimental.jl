`filelist(dir::SFTPClient.SFTP [, subdir])` は SFTP ディレクトリのファイルリストを返します。この関数は `SFTPClient` の `Base.readdir(sftp::SFTP, join::Bool = false, sort::Bool = true)` を利用します。

この関数は現在 `join` および `sort` 引数をサポートしていません。なぜなら、`sftpstat` に依存してパスがファイルかどうかを確認するためですが、`sftpstat` は常にソートされていない結果と結合されていない結果を返すからです。
