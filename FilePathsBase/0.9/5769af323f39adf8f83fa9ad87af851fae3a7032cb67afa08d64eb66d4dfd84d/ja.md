```
AbstractPath
```

抽象ファイルシステムパスを定義します。

# プロパティ

  * `segments::Tuple{Vararg{String}}` - パスセグメント（必須）
  * `root::String` - パスのルート（デフォルトは "/"）
  * `drive::String` - パスのドライブ（デフォルトは ""）
  * `separator::String` - パスのセパレーター（デフォルトは "/"）

# 必要なメソッド

  * `tryparse(::Type{T}, str::String)` - パスの文字列表現を解析するため
  * `read(path::T)`
  * `write(path::T, data)`
  * `exists(path::T)` - パスが存在するかどうか
  * `stat(path::T)` - 権限、サイズ、作成/変更時刻を説明するファイルステータス
  * `mkdir(path::T; kwargs...)` - 新しいディレクトリを作成
  * `rm(path::T; kwags...)` - ファイルまたはディレクトリを削除
  * `readdir(path::T)` - 特定のパスレベルでのすべてのファイルとディレクトリをスキャン
