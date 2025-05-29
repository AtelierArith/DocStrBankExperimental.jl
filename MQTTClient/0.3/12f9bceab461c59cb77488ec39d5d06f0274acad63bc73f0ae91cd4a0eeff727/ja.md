```
IOConnection(ip::IPAddr, port::Int64)
```

指定されたIPアドレスとポート番号で新しい`TCP`オブジェクトを構築します。

# 引数

  * `ip::IPAddr`: リモートホストのIPアドレス。
  * `port::Int64`: リモートホストのポート番号。

# 戻り値

  * `TCP`: 新しい`TCP`オブジェクト。
  *   *   *

    IOConnection(ip::String, port::Int64)

指定されたIPアドレスとポート番号で新しい`TCP`オブジェクトを構築します。

# 引数

  * `ip::String`: 文字列としてのリモートホストのIPアドレス。
  * `port::Int64`: リモートホストのポート番号。

# 戻り値

  * `TCP`: 新しい`TCP`オブジェクト。
  *   *   *

    IOConnection(path::AbstractString)

指定されたファイルシステムパスで新しい`UDS`オブジェクトを構築します。

# 引数

  * `path::AbstractString`: ソケットのファイルシステムパス。

# 戻り値

  * `UDS`: 新しい`UDS`オブジェクト。
