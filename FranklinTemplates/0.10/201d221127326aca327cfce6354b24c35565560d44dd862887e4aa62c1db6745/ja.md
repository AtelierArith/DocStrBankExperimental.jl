```
newsite(topdir; template="basic", cd=true)
```

Franklinで処理できるウェブサイトのスケルトンを含む新しいフォルダーを生成します（既に存在する場合はエラーが発生します）。ユーザーは利用可能なテンプレートのリストから`template`を指定できます。`topdir`が `"."` と指定されている場合、現在のディレクトリが使用されます。

  * `template="basic"`: 使用するテンプレートの名前、
  * `cd=true`:          新しく作成されたフォルダーに現在のディレクトリを変更するかどうか。
  * `verbose=true`:     情報を表示するかどうか。

### 例

```julia
newsite("MyNewWebsite", template="pure-sm")
```
