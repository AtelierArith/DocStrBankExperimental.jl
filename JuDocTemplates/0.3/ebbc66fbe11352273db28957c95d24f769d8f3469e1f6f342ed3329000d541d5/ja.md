```
newsite(topdir; template="basic", cd=true)
```

JuDocで処理できるウェブサイトのスケルトンを含む新しいフォルダーを生成します（既に存在する場合はエラーが発生します）。ユーザーは利用可能なテンプレートのリストから`template`を指定できます。

  * `template="basic"` 希望するテンプレートの名前を指定します。
  * `cd=true` 新しく作成されたフォルダーに現在のディレクトリを変更するかどうかを指定します。
  * `verbose=true` 情報を表示するかどうかを指定します。

### 例

```julia
newsite("MyNewWebsite", template="pure-sm")
```
