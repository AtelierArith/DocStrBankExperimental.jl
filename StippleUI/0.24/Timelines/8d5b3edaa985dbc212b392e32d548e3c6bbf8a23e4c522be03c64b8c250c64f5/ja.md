```
  timelineentry(args...; kwargs...)
```

---

### 例

---

### 表示

```julia-repl
julia> timelineentry(title="イベントタイトル", subtitle="1986年2月21日", icon="delete",[
            Html.div("Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                  sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                  nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                  reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
                  Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia
                  deserunt mollit anim id est laborum.")
       ])
```

---

### 引数

---

1. 動作

      * `side::String` - タイムラインエントリを配置する側; `timeline` レイアウトが緩い場合のみ機能します。 (デフォルト: `"right"`) | 例: `"left"` | `"right"`
2. コンテンツ

      * `tag::String` - 使用するタグ、タイプが 'heading' の場合のみ。 (デフォルト: `"h3"`) | 例: `"h1"` | `"h2"` | `"h3"` | `"h4"` | `"h5"` | `"h6"`
      * `heading::Bool` - ヘッディングタイムラインアイテムを定義します
      * `icon::String` - Quasar 規約に従ったアイコン名; 'img:' プレフィックスを使用していない限り、アイコンライブラリがインストールされていることを確認してください; 'none' (String) が値として使用されると、アイコンは表示されません (ただし、画面の実際のスペースは依然として使用されます)。 (例: `"map"` | `"ion-add"`)
      * `avatar::String` - アバター画像のURL; アイコンが使用される場合は優先され、アバターが置き換えられます。
      * `title::String` - タイムラインエントリのタイトル; 'title' スロットを使用する場合は上書きされます
      * `subtitle::String` - タイムラインエントリのサブタイトル; 'subtitle' スロットを使用する場合は上書きされます
      * `body::String` - タイムラインエントリの本文コンテンツ; このプロパティまたはデフォルトスロットを使用します
3. スタイル

      * `color::String` - Quasar カラーパレットからのコンポーネントの色名
