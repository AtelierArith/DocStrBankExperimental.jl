```
  uploader(args...; kwargs...)
```

Stippleは、`uploader`コンポーネントを通じてファイルをアップロードする方法を提供します。

---

### 例

---

### 表示

```julia-repl
julia> uploader(label="画像をアップロード", autoupload=true, multiple=true, method="POST", url="/upload", field__name="img")
```

---

### 引数

---

1. 動作

      * `multiple::Bool` - 複数のファイルアップロードを許可
      * `accept::String` - 一意のファイルタイプ指定子のカンマ区切りリスト。ネイティブのinput type=file要素の'accept'属性にマップされます。例: `.jpg, .pdf, image/*` `image/jpeg, .pdf`
      * `capture::String` - オプションで、新しいファイルをキャプチャする必要があり、どのデバイスを使用してその新しいメディアをキャプチャするかを指定します。'accept'プロパティで定義されたタイプにマップされます。ネイティブのinput type=file要素の'capture'属性にマップされます。例: `user` `environment`
      * `maxfilesize::Union{Int, String}` - 個々のファイルの最大サイズ（バイト単位）例: `1024` `1048576`
      * `maxtotalsize::Union{Int, String}` - 結合されたすべてのファイルの最大サイズ（バイト単位）例: `1024` `1048576`
      * `maxfiles::Union{Int, String}` - 含むことができるファイルの最大数例: `maxfiles!="5"` `10`
      * `filter::Function` - 追加されたファイルのカスタムフィルター; このフィルターを通過したファイルのみがキューに追加され、アップロードされます; 最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。例: `filter!="files => files.filter(file => file.size === 1024)"`
      * `autoupload::Bool` - 追加されたときにファイルを即座にアップロード
      * `hideuploadbtn::Bool` - アップロードボタンを表示しない
2. コンテンツ

      * `label::Union{String,Symbol,Nothing}` - アップローダーのラベル例: `ここに写真をアップロード`
      * `nothumbnails::Bool` - 画像ファイルのサムネイルを表示しない
3. 状態

      * `disable::Bool` - コンポーネントを無効モードにする
      * `readonly::Bool` - コンポーネントを読み取り専用モードにする
4. スタイル

      * `color:String` - コンポーネントの色 [カラーパレット](https://quasar.dev/style/color-palette) から例: `primary` `teal-10`
      * `textcolor::String` - テキストの色をオーバーライド（必要に応じて）; [カラーパレット](https://quasar.dev/style/color-palette) からの色名例: `primary` `teal-10`
      * `dark::Bool` - ダークモード
      * `square::Bool` - ボーダー半径を削除し、ボーダーを四角にする
      * `flat::Bool` - フラットデザインを適用（デフォルトの影なし）
      * `bordered::Bool` - コンポーネントにデフォルトのボーダーを適用
5. アップロード

      * `url::String` - アップロードを処理するサーバーのURLまたはパス。文字列または文字列を返すファクトリ関数を取ります。関数はアップロードの直前に呼び出されます; 関数を使用する場合は、最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。例: `"files => https://example.com?count=:({files.length})"` `https://example.com/path`
      * `method::String` - アップロードに使用するHTTPメソッド; 文字列または文字列を返すファクトリ関数を取ります; 関数はアップロードの直前に呼び出されます; 関数を使用する場合は、最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。デフォルト: `POST` 例: `POST` `PUT`
      * `fieldname::String` - 各ファイルアップロードのフィールド名; これは次のヘッダーに入ります: 'Content-Disposition: form-data; name="**HERE**"; filename="somefile.png"; 関数を使用する場合は、最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。デフォルト値: `(file) => file.name` 例: `backgroundFile` `fieldname!="(file) => 'background' + file.name"`
      * `headers::Union{Vector{Dict(String, String)}, String}` - 配列または配列を返すファクトリ関数; 配列はヘッダー定義を持つオブジェクトで構成されます; 関数はアップロードの直前に呼び出されます; 関数を使用する場合は、最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。例: `[{name: 'Content-Type', value: 'application/json'}, {name: 'Accept', value: 'application/json'}]`
      * `formfields::Union{Vector{Dict(String, String)}, String}` - 配列または配列を返すファクトリ関数; 配列は追加フィールド定義を持つオブジェクトで構成されます（アップロードされるフォームによって使用されます）; 関数はアップロードの直前に呼び出されます; 関数を使用する場合は、最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。例: `[{name: 'my-field', value: 'my-value'}]`
      * `with-credentials::Union{Bool, String}` - アップロードを管理するXHRでwithCredentialsをtrueに設定します; ブール値またはブールのファクトリ関数を取ります; 関数はアップロードの直前に呼び出されます; 関数を使用する場合は、最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。例: `with-credentials` `with!="files => ...."`
      * `sendraw::Union{Bool, String}` - フォームにラップせずに生ファイルを送信します; ブール値またはブールのファクトリ関数を取ります; 関数はアップロードの直前に呼び出されます; 関数を使用する場合は、最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。例: `sendraw` `sendraw!="files => ...."`
      * `batch::Union{Bool, String}` - バッチでファイルをアップロードします（1つのXHRリクエストで）; ブール値またはブールのファクトリ関数を取ります; 関数はアップロードの直前に呼び出されます; 関数を使用する場合は、最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。例: `"files => files.length > 10"`

```
