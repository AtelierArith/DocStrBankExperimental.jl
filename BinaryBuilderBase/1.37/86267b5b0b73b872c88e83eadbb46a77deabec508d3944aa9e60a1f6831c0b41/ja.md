```
package(prefix::Prefix, output_base::AbstractString,
        version::VersionNumber;
        platform::AbstractPlatform = HostPlatform(),
        verbose::Bool = false, force::Bool = false,
        filter = Returns(true))
```

`prefix`のtarballをビルドし、`output_base`にtarballを保存し、バージョン番号`version`、プラットフォーム依存のサフィックス、およびファイル拡張子を追加します。`platform`が指定されていない場合は、現在のプラットフォームがデフォルトとなります。生成されたtarballのフルパス、SHA256ハッシュ、およびgitツリーSHA1を返します。

追加のキーワード引数があります：

  * `verbose`は、情報を画面に表示するかどうかを制御します。
  * `force`は、同じ名前の既存のtarballを上書きするように関数を設定します。
  * `filter`は2引数の関数で、指定されたファイルまたはディレクトリをパッケージ化すべき場合は`true`を、そうでない場合は`false`を返します。引数は`(prefix, path)`で、`prefix`はプレフィックスが保存されているディレクトリであり、`path`はプレフィックス内のファイルまたはディレクトリのパスです。このキーワードを使用すると、tarballから特定のファイルやディレクトリを除外できます。
