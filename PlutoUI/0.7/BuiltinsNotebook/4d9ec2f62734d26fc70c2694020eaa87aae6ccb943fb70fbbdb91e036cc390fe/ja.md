ファイルアップロードボックス。選択されたファイルはブラウザによって読み込まれ、そのバイトがJuliaに送信されます。

オプションの`accept`引数は`MIME`の配列であることができます。ユーザーはこれらのMIMEを持つファイルのみを選択できます。もし`image/*` MIMEのみが許可されている場合、スマートフォンのブラウザはファイルブラウザの代わりにカメラを開きます。

## 例

`@bind file_data FilePicker()`

`file_data["data"]`

許可されるMIMEタイプを制限することができます：

```julia
@bind image_data FilePicker([MIME("image/jpg"), MIME("image/png")])
# そしてMIMEグループを使用します：
@bind image_data FilePicker([MIME("image/*")])
```
