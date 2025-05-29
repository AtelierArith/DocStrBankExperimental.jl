```
dcc_upload(;kwargs...)
dcc_upload(children::Any, kwargs...)
dcc_upload(children_maker::Function, kwargs...)
```

アップロードコンポーネント アップロードコンポーネントは、アプリがユーザーがアップロードしたファイルをドラッグ＆ドロップで受け入れることを可能にします。

  * `children` (ダッシュコンポーネント、文字列または数値のリストまたは単一 | String; オプション): アップロードコンポーネントの内容
  * `id` (String; オプション): このコンポーネントのIDで、ダッシュコンポーネントをコールバックで識別するために使用されます。IDはアプリ内のすべてのコンポーネントで一意である必要があります。
  * `accept` (String; オプション): 特定のタイプのファイルを許可します。

詳細については https://github.com/okonet/attr-accept を参照してください。mimeタイプの決定はプラットフォーム間で信頼性がないことに注意してください。たとえば、CSVファイルはmacOSではtext/plainとして報告されますが、Windowsではapplication/vnd.ms-excelとして報告されます。場合によっては、mimeタイプが全く設定されていないこともあります。参照: https://github.com/react-dropzone/react-dropzone/issues/276

  * `className` (String; オプション): コンポーネントのHTMLクラス名
  * `className_active` (String; オプション): アクティブなときのコンポーネントのHTMLクラス名
  * `className_disabled` (String; オプション): 無効な場合のコンポーネントのHTMLクラス名
  * `className_reject` (String; オプション): 拒否された場合のコンポーネントのHTMLクラス名
  * `contents` (String | Array of Strings; オプション): アップロードされたファイルの内容をバイナリ文字列として
  * `disable_click` (Bool; オプション): コンポーネントをクリックしてファイルダイアログを開くことを禁止
  * `disabled` (Bool; オプション): アップロードコンポーネントを完全に有効/無効にする
  * `filename` (String | Array of Strings; オプション): アップロードされたファイルの名前。

これはファイルのパスを含まないことに注意してください（セキュリティ上の理由から）。

  * `last_modified` (Array of s; オプション): アップロードされたファイルの最終更新日をUnix時間で

（1970年以降の秒数）。

  * `loading_state` (要素を含むリスト is*loading, prop*name, component*name   - `is*loading`(Bool; オプション): コンポーネントが読み込み中かどうかを判断   -`prop*name`(String; オプション): どのプロパティが読み込み中かを保持   -`component*name` (String; オプション): 読み込み中のコンポーネントの名前を保持; オプション): dash-rendererからの読み込み状態オブジェクトを保持するオブジェクト
  * `max_size` (オプション): 最大ファイルサイズ（バイト単位）。 `-1`の場合、無限
  * `min_size` (オプション): 最小ファイルサイズ（バイト単位）
  * `multiple` (Bool; オプション): 複数のファイルのドロップを許可
  * `style` (Dict; オプション): 適用するCSSスタイル
  * `style_active` (Dict; オプション): アクティブなときに適用するCSSスタイル
  * `style_disabled` (Dict; オプション): 無効な場合のCSSスタイル
  * `style_reject` (Dict; オプション): 拒否された場合のCSSスタイル
